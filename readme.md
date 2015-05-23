My frustration comes from seeing this massive list of hardcoded times.

As a fun project, I’ve decided to rewrite this to couple of lines of code.

First step - listing all time slots from 00:00 23:30.

    public List<SelectOption> timeslots {
        get {
            List<SelectOption> options = new List<SelectOption>();
            options.add(new SelectOption('12:00 AM','12:00 AM'));
            options.add(new SelectOption('12:30 AM','12:30 AM'));
            options.add(new SelectOption('1:00 AM','1:00 AM'));
            options.add(new SelectOption('1:30 AM','1:30 AM'));
            options.add(new SelectOption('2:00 AM','2:00 AM'));
            options.add(new SelectOption('2:30 AM','2:30 AM'));
            options.add(new SelectOption('3:00 AM','3:00 AM'));
            options.add(new SelectOption('3:30 AM','3:30 AM'));
            options.add(new SelectOption('4:00 AM','4:00 AM'));
            options.add(new SelectOption('4:30 AM','4:30 AM'));
            options.add(new SelectOption('5:00 AM','5:00 AM'));
            options.add(new SelectOption('5:30 AM','5:30 AM'));
            options.add(new SelectOption('6:00 AM','6:00 AM'));
            options.add(new SelectOption('6:30 AM','6:30 AM'));
            options.add(new SelectOption('7:00 AM','7:00 AM'));
            options.add(new SelectOption('7:30 AM','7:30 AM'));
            options.add(new SelectOption('8:00 AM','8:00 AM'));
            options.add(new SelectOption('8:30 AM','8:30 AM'));
            options.add(new SelectOption('9:00 AM','9:00 AM'));
            options.add(new SelectOption('9:30 AM','9:30 AM'));
            options.add(new SelectOption('10:00 AM','10:00 AM'));
            options.add(new SelectOption('10:30 AM','10:30 AM'));
            options.add(new SelectOption('11:00 AM','11:00 AM'));
            options.add(new SelectOption('11:30 AM','11:30 AM'));
            options.add(new SelectOption('12:00 PM','12:00 PM'));
            options.add(new SelectOption('12:30 PM','12:30 PM'));
            options.add(new SelectOption('1:00 PM','1:00 PM'));
            options.add(new SelectOption('1:30 PM','1:30 PM'));
            options.add(new SelectOption('2:00 PM','2:00 PM'));
            options.add(new SelectOption('2:30 PM','2:30 PM'));
            options.add(new SelectOption('3:00 PM','3:00 PM'));
            options.add(new SelectOption('3:30 PM','3:30 PM'));
            options.add(new SelectOption('4:00 PM','4:00 PM'));
            options.add(new SelectOption('4:30 PM','4:30 PM'));
            options.add(new SelectOption('5:00 PM','5:00 PM'));
            options.add(new SelectOption('5:30 PM','5:30 PM'));
            options.add(new SelectOption('6:00 PM','6:00 PM'));
            options.add(new SelectOption('6:30 PM','6:30 PM'));
            options.add(new SelectOption('7:00 PM','7:00 PM'));
            options.add(new SelectOption('7:30 PM','7:30 PM'));
            options.add(new SelectOption('8:00 PM','8:00 PM'));
            options.add(new SelectOption('8:30 PM','8:30 PM'));
            options.add(new SelectOption('9:00 PM','9:00 PM'));
            options.add(new SelectOption('9:30 PM','9:30 PM'));
            options.add(new SelectOption('10:00 PM','10:00 PM'));
            options.add(new SelectOption('10:30 PM','10:30 PM'));
            options.add(new SelectOption('11:00 PM','11:00 PM'));
            options.add(new SelectOption('11:30 PM','11:30 PM'));
            return options;
        }
    }
    <code>
    public SelectOption[] timeslot2 {
        get {
            SelectOption[] options = new SelectOption[]{};
            string temp;
            for (integer i = 0, j = 48; i<j;i++){
                if(math.mod(i,2)==0){
                    temp = string.valueOf(0+i/2);
                    if (i<20){temp='0'+temp;}
                    options.add(new SelectOption(temp+':00’,temp+':00’));
                } else {
                    options.add(new SelectOption(temp+’:30’,temp+’:30’));
                }   
            }
            return options;
        }
    }
    </code>

    Got a better solution:
    <code>string[] dates = new string[]{};
        for (Integer i = 0, j = 0; i < 10; i++){
            dates.add(DateTime.newInstance(0L).addMinutes(30*i).format('HH:mm a'));}
    system.debug(dates);</code>

Basically using Java date format parameters simplifies things a bit. Did some benchmarking using methods shown in Paul Battison videos and this last technique takes a tiny bit more CPU time. You could though instantiate only one dateTime variable, and then keep adding 30 minutes to it.
