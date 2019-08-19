<Container>
<h1>About Timeline</h1>
    <Container>
            <h2>Demo 1</h2>
            <Timeline >
                <TimelineItem side='left' icon='' backgroundColor="rgb(59, 95, 59)">
                    <h2>Left school</h2>
                    <p>Started drinking and smoking</p>
                </TimelineItem>
                <TimelineItem side='left' icon='' backgroundColor="green"><h2>Left university</h2><p>Continued drinking and smoking</p></TimelineItem>
                <TimelineItem side='right' icon=''><h2>Left school</h2><p>Stopped drinking and smoking</p></TimelineItem>
                <TimelineItem side='right' icon='' backgroundColor="rgb(59, 195, 59)"><h2>Kept smoking</h2><p>Then started drinking and smoking again</p></TimelineItem>
        </Timeline>
    </Container>

    <Container>
        <h2>Demo 2</h2>
        <Timeline items={timelineItems} style="background-color:red">
        </Timeline>
    </Container>
</Container>

<script>
    import { Accordian, Checkbox, Container, Counter, DatePicker, 
        Form, Section, StarRatTimelineing, TimelineItem
        } from "../components/index.js";

    let timelineItems = [
    {   side:"left",  icon: "",   content:"<h2>Left school</h2><p>Started drinking and smoking</p>"       },
    {   side:"right", icon: "",   content:"<h2>Left university</h2><p>Continued drinking and smoking</p>"       },
    {   side:"right", icon: "",   content:"<h2>Got job</h2><p>Started drinking and smoking</p>"       },
    {   side:"left",  icon: "",   content:"<h2>Lost job</h2><p>Continued drinking and smoking</p>"       },
    {   side:"right", icon: "",   content:"<h2>Got UBI</h2><p>Kept smoking</p>"       },
    ];
</script>

<style>
    h1 {
        color: brown;
    }
</style>
