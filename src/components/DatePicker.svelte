<script>
    import { createEventDispatcher, onMount } from "svelte";

    const today = new Date();
    const dispatch = createEventDispatcher();
    const weekdays = [7, 6, 5, 4, 3, 2, 1];

    export let month = today.getMonth();
    export let year = today.getFullYear();
    export let format = "DD/MM/YYYY HH:mm:ss";
    export let datetime = false;
    export let cancelonsubmit = true;
    export let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];

    let picked_date;
    let hours = "";
    let minutes = "";
    let weeks = {};
    let week_numbers = {};
    let cancel_btn;

    if (months.length !== 12) {
        throw new Error("Supplied months array did not contain 12 elements.");
    }

    // Returns the ISO week of the date.
    Date.prototype.getWeek = function() {
            const date = new Date(this.getTime());
            date.setHours(0, 0, 0, 0);
            // Thursday in current week decides the year.
            date.setDate(date.getDate() + 3 - (date.getDay() + 6) % 7);
            // January 4 is always in week 1.
            const week1 = new Date(date.getFullYear(), 0, 4);
            // Adjust to Thursday in week 1 and count number of weeks from date to week1.
            return 1 + Math.round(((date.getTime() - week1.getTime()) / 86400000 - 3 + (week1.getDay() + 6) % 7) / 7);
    };

    // Returns the four-digit year corresponding to the ISO week of the date.
    Date.prototype.getWeekYear = function() {
            const date = new Date(this.getTime());
            date.setDate(date.getDate() + 3 - (date.getDay() + 6) % 7);
            return date.getFullYear();
    };

    /**
     * @param {number} month - The month number, 0 based.
     * @param {number} year - The year, not zero based, required to account for leap years.
     * @return {Date[]} - List with date objects for each day of the month.
     */
    function month_days(month, year) {
        const date = new Date(year, month, 1);
        let days = [];
        while (date.getMonth() === month) {
            days.push(new Date(date));
            date.setDate(date.getDate() + 1);
        }
        return days;
    }

    /**
     * Decrements the active month accounting for year underflow.
     */
    function dec_month() {
        month -= 1;
        if (month < 0) {
            month = 11;
            year --;
        }
    }

    /**
     * Increments the active month accounting for year overflow.
     */
    function inc_month() {
        month += 1;
        if (month > 11) {
            month = 0;
            year ++;
        }
    }

    /**
     * Returns the final date of a year + month combination.
     */
    function final_day_of_month(year, month) {
        return new Date(year, month + 1, 0);
    }

    /**
     * Builds a date for a date in the month after a supplied month.
     *
     * @param {number} year - Year of the date.
     * @param {number} month - Month of the date, will be incremented.
     * @param {number} date - Date of the date next month.
     * @returns {Date} - Date object of a given day in the month after the
     * supplied month.
     */
    function day_x_next_month(year, month, date) {
        month = month + 1;
        return new Date(year, month, date);
    }

    /**
     * Checks the equivalency of two date objects
     *
     * @param {Date} date - First date.
     * @param {Date} [cmp_date] - Second date. If ommited will default to a `new
     * Date` object (today).
     * @returns {boolean} - Whether the two dates are equivalent.
     */
    function is_same_date(date, cmp_date) {
        if (!date) {
            return false;
        }
        cmp_date = !!cmp_date ? cmp_date : today;
        return date.getFullYear() === cmp_date.getFullYear()
            && date.getMonth() === cmp_date.getMonth()
            && date.getDate() === cmp_date.getDate();
    }

        function pad(s) {
                return s.length === 1 ? `0${s}` : s;
        }

    /**
     * Given a supplied month will return the month before it, accounting for
     * year underflow.
     *
     * @param {number} month - Month to get the previous month for.
     * @returns {number} - Index of the previous month.
     */
    function prev_month(month) {
        return month === 0 ? 11 : month - 1;
    }

    /**
     * Given a supplied month will return the month after it, accounting for
     * year overflow.
     *
     * @param {number} month - Month to get the following month for.
     * @returns {number} - Index of the following month.
     */
    function next_month(month) {
        return month === 11 ? 0 : month + 1;
    }

    /**
     * Send a date, and cancel event if cancelonsubmit is true, to the parent.
     */
    function submit_date() {
        if (!picked_date || datetime && (!minutes_valid || !hours_valid)) {
            return;
        }

        if (datetime) {
            picked_date.setHours(hours);
            picked_date.setMinutes(minutes);
        }

        hours = hours === "" ? "00" : hours;
        hours = hours.length === 1 ? `0${hours}` : hours;
        minutes = minutes === "" ? "00" : minutes;
        minutes = minutes.length === 1 ? `0${minutes}` : minutes;

        const formatted_date = format
            .replace("DD", pad(picked_date.getDate()))
            .replace("MM", pad(picked_date.getMonth() + 1))
            .replace("YYYY", picked_date.getFullYear())
            .replace("yyyy", `${picked_date.getFullYear()}`.substring(2, 4))
            .replace("HH", pad(hours))
            .replace("H", hours)
            .replace("mm", pad(minutes))
            .replace("m", minutes)
            .replace("ss", "00")

        dispatch("date", {
            date: formatted_date,
            date_object: picked_date,
        });

        if (cancelonsubmit) {
            cancel();
        }
    }

    /**
     * Sends a cancel event to the parent. Is triggered by pressing the "X"
     * button while `datetime` is true or by pressing the escape key. Due to the
     * nature of some parents a click event might unintentionally be passed on
     * to this component, hence why the `e.explicitOriginalTarget` check and
     * cancel_btn binding are necessary.
     *
     * @param {Event} [e] - DOM event. Used for verifying the origin of the event.
     * If the event, such as click or mousedown, did not originate from the
     * cancel button itself a cancel event is not dispatched. If no event is
     * provided the cancel event is always dispatched.
     */
    function cancel(e) {
        if (e) {
            if (e.explicitOriginalTarget !== cancel_btn) {
                return;
            }
        }
        dispatch("cancel");
    }

    /**
     * Executes when a date is clicked. If `datetime` is not true the date event
     * is dispatched.
     */
    function handle_date_click(date) {
        picked_date = date;
        if (!datetime) {
            submit_date();
        }
    }

    onMount(() => {
        // Add Escape and Enter shortcuts.
        window.addEventListener("keydown", (event) => {
            if (event.key === "Escape") {
                cancel();
            } else if (event.key === "Enter") {
                submit_date();
            }
        });
    });

    // Dynamically updated list of active month days.
    $: this_month_days = month_days(month, year);
    // String identifier of the active month.
    $: month_string = months[month % months.length];
    // Whether the supplied minutes are valid in a datetime.
    $: minutes_valid = !!pad(minutes).match(/([0-5][0-9])/);
    // Whether the supplied hours are valid in a datetime.
    $: hours_valid = !!pad(hours).match(/(00|01|02|03|04|05|06|07|08|09|10|11|12|13|14|15|16|17|18|19|20|21|22|23)/);
    // Dynamically updated list of week numbers containing dates for the given
    // month.
    $: {
        weeks = {};
        week_numbers = [];
        let last_week = -1;
        this_month_days.forEach((day) => {
            const week_number = `${day.getWeek()}`;
            if (!Object.keys(weeks).includes(week_number)) {
                weeks[week_number] = [];
            }
            if (week_number != last_week) {
                week_numbers.push(week_number);
                last_week = week_number;
            }
            weeks[week_number].push(day);
        });
        //console.log(week_numbers);
        //console.log(weeks);
    }
</script>

<div class="datepicker">
    <div class="header">
        <span class="prev  prevyear chevron" on:click={()=>year--}>&laquo;</span>
        <div class="prev" on:click={dec_month}>
            <span class="chevron">&lsaquo;</span>
            <span class="month">
                {months[(month > 0 ? month - 1 : 11) % months.length].substring(0, 3)}
            </span>
        </div>
        <span class="current-month">{month_string} {year}</span>
        <div class="next" on:click={inc_month}>
            <span class="month">
                {months[(month + 1) % months.length].substring(0, 3)}
            </span>
            <span class="chevron">&rsaquo;</span>
        </div>
        <span class="next nextyear chevron" on:click={()=>year++}>&raquo;</span>
    </div>
    <table>
        <thead>
            <tr>
                <th>#</th>
                <th>Mon</th>
                <th>Tue</th>
                <th>Wed</th>
                <th>Thu</th>
                <th>Fri</th>
                <th>Sat</th>
                <th>Sun</th>
            </tr>
        </thead>
        <tbody>
            {#each week_numbers as week_number}
                <tr class="week">
                    {#if month !== 11 || week_number !== "1"}
                        <td class="week-number">{week_number}</td>
                        {#each weeks[week_number] as date}
                            {#if date.getDate() === 1}
                                {#each weekdays.slice(weeks[week_number].length) as i}
                                    <td
                                        class="date disabled"
                                        class:today={is_same_date(new Date(year, month, 1 - i))}
                                        class:picked={is_same_date(picked_date, new Date(year, month, 1 - i))}
                                        on:click={() => handle_date_click(new Date(year, month, 1 - i))}
                                    >
                                        {new Date(new Date().setDate(weeks[week_number][0].getDate() - i)).getDate()}
                                    </td>
                                {/each}
                            {/if}
                            <td
                                class="date"
                                class:picked={is_same_date(picked_date, date)}
                                class:today={is_same_date(date)}
                                on:click={() => handle_date_click(date)}
                            >
                                {date.getDate()}
                            </td>
                            {#if date.getDate() === final_day_of_month(date.getFullYear(), date.getMonth()).getDate()}
                                {#each weekdays.slice(weeks[week_number].length) as _, i}
                                    <td
                                        class="date disabled"
                                        class:today={is_same_date(day_x_next_month(year, month, i + 1))}
                                        class:picked={is_same_date(picked_date, day_x_next_month(year, month, i + 1))}
                                        on:click={() => handle_date_click(day_x_next_month(year, month, i + 1))}
                                    >
                                        {i + 1}
                                    </td>
                                {/each}
                            {/if}
                        {/each}
                    {/if}
                </tr>
            {/each}
            <!-- handle the last week in Dec overflowing into week 1 of the next year -->
            {#if month === 11 && weeks["1"]}
                <td class="week-number">1</td>
                {#each weeks["1"] as date}
                    <td
                        class="date"
                        class:picked={is_same_date(picked_date, date)}
                        class:today={is_same_date(date)}
                        on:click={() => handle_date_click(date)}
                    >
                        {date.getDate()}
                    </td>
                    {#if date.getDate() === final_day_of_month(date.getFullYear(), date.getMonth()).getDate()}
                        {#each weekdays.slice(weeks["1"].length) as _, i}
                            <td
                                class="date disabled"
                                class:today={is_same_date(day_x_next_month(year, month, i + 1))}
                                class:picked={is_same_date(picked_date, day_x_next_month(year, month, i + 1))}
                                on:click={() => handle_date_click(day_x_next_month(year, month, i + 1))}
                            >
                                {i + 1}
                            </td>
                        {/each}
                    {/if}
                {/each}
            {/if}
        </tbody>
    </table>
    <div class="footer">
        {#if datetime}
            <button class="footer-btn cancel" on:click={cancel} bind:this={cancel_btn}>&#xd7;</button>
            <div class="timepicker">
                <input
                    type="text"
                    pattern="(00|01|02|03|04|05|06|07|08|09|10|11|12|13|14|15|16|17|18|19|20|21|22|23)"
                    class="numerical"
                    placeholder="00"
                    bind:value={hours}
                    on:input={() => hours = hours.length > 2 ? hours.substring(0, 2) : hours}
                    on:blur={() => hours = pad(hours)}
                />
                    :
                <input
                    type="text"
                    pattern="([0-5][0-9])"
                    class="numerical"
                    placeholder="00"
                    bind:value={minutes}
                    on:input={() => minutes = minutes.length > 2 ? minutes.substring(0, 2) : minutes}
                    on:blur={() => minutes = pad(minutes)}
                />
            </div>
            <button
                class="footer-btn submit"
                class:disabled={!minutes_valid || !hours_valid || !picked_date}
                on:click={submit_date}
            >
                &#x2713;
            </button>
        {/if}
    </div>
</div>

<style>
    .datepicker {
            display: flex;
            flex-direction: column;
            width: 315px;
            background-color: white;
            box-shadow: 0 5px 10px 2px rgba(0, 0, 0, 0.3);
            position:absolute;
            z-index:1;
    }

    .datepicker .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 5px;
            font-size: var(--navfontsize);
            text-transform: uppercase;
            color: var(--navforeground);
            font-weight: bold;
            background-color: var(--navbackground);
    }

    .datepicker .header .next,
    .datepicker .header .prev {
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: color 0.15s linear;
            font-size: 14px;
            width: 35px;
            padding: 0 10px;
            height: 40px;
    }

    .datepicker .header .nextyear,
    .datepicker .header .prevyear {
            width: 15px;
    }


    .datepicker .header .next:hover,
    .datepicker .header .prev:hover {
            background-color: var(--navbackgroundhover);
    }

    .datepicker .header .next .chevron,
    .datepicker .header .prev .chevron {
            margin-top: -4px;
            font-size: 14px;
    }

    .datepicker .header .next {
            text-align: right;
    }

    .datepicker .header .next .month {
            margin-right: 5px;
    }

    .datepicker .header .prev {
            text-align: left;
    }

    .datepicker .header .prev .month {
            margin-left: 5px;
    }

    .datepicker table {
            width: 100%;
    }

    .datepicker table * {
            text-align: center;
    }

    .datepicker table td {
            width: 35px;
            height: 35px;
            font-size: 16px;
            border : 0px;
    }

    .datepicker table th {
            padding: 4px;
            border : 0px;
    }
    .datepicker tr:nth-child(even) {
        background-color: white;
    }
    .datepicker tr:hover  {
        background-color: white;
    }

    .datepicker table td:not(.week-number) {
            cursor: pointer;
    }

    .datepicker table td:not(.week-number).today {
            background-color: #7dabca;
    }

    .datepicker table td:not(.week-number):hover,
    .datepicker table td:not(.week-number).picked {
            background-color: var(--navbackgroundhover);
            color: var(--navforegroundhover); 
    }

   .datepicker table td:not(.week-number).disabled:not(.picked):not(.today) {
            color: #aaa;
    }

    .datepicker table td.week-number {
            font-weight: bold;
    }

    .footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 5px;
    }

    .footer .timepicker {
            display: flex;
            align-items: center;
            justify-content: center;
            justify-self: center;
    }

    .footer .timepicker * {
            font-size: 22px;
    }

    .footer .timepicker input.numerical {
            width: 45px;
            border: none;
            border-bottom: 1px solid #aaa;
            padding: 0 5px;
            text-align: center;
    }

    .footer .footer-btn {
            height: 28px;
            width: 28px;
            color: white;
            font-weight: bold;
            border: none;
            cursor: pointer;
    }

    .footer .footer-btn.submit {
            background-color: #0681ff;
    }

    .footer .footer-btn.submit:hover {
            background-color: #0068d2;
    }

    .footer .footer-btn.submit.disabled {
            cursor: default;
            background-color: #797979;
    }

    .footer .footer-btn.submit.disabled:hover {
            background-color: #797979;
    }

    .footer .footer-btn.cancel {
            background-color: #797979;
    }

    .footer .footer-btn.cancel:hover {
            background-color: #6b6b6b;
    }
</style>