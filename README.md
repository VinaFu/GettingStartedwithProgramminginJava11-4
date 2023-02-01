# GettingStartedwithProgramminginJava11-4

8. String Formatting - Concatenation VS. Formatting
  
   [[ Flag ]] && [[ Argument]]
  
        Concatenation - combine different variables (and strings) together.
        Formatting - String.format() method returns a formatted string using the given locale, specified format string, and arguments. usually seen as %
    
e.g
    
       int david = 17, dawson = 15, dillon = 8, gordon = 6;
           double avgDiff = ((david - dawson) + (dawson - dillon) + (dillon -gordon)) / 3.0d;
           String s4 = String.format(
                   "The average are between each is %.1f years", avgDiff
           );  // % means quote the avgDiff;
               //1f refers to a floating point number, with 1 digit after the decimal (the .)
           System.out.println(s4);     // The average are between each is 3.7 years
        
Common format conversions   
     
        %d - decimal - interger
        %f - floating 
                %2f - round it to 2 decimal places
        %s - string
        %# - flag with x or X - integer hexadecimal
        
Format Specificer

       % [flags] [width] [.precision] [argsize] typechar

        
      int iVal = 32;
        String s1 = String.format("%d", iVal);
        String s2 = String.format("%x", iVal);
        String s3 = String.format("%#x", iVal);
        String s4 = String.format("%#X", iVal);
        System.out.println(s1);
        System.out.println(s2);
        System.out.println(s3);
        System.out.println(s4);
            // 32
            // 20
            // 0x20
            // 0X20
        
[%04d]:

        int w = 5, y = 481, x = 235, z = 12;
        String s1 = String.format("W:%d  X:%d", w, x);
            // W:5  X:235
            // use % to define digits
            // don't forget ""
        System.out.println(s1);
            // W:5  X: 235
                
        String s1 = String.format("W:%4d  X:%4d", w, x);
        String s2 = String.format("Y:%4d  Z:%4d", y, z);
            // "%4d"
        System.out.println(s1);
        System.out.println(s2);
            // W:   5  X: 235
            // Y: 481  Z:  12        
        
        String s1 = String.format("W:%04d  X:%04d", w, x);
        String s2 = String.format("Y:%4d  Z:%4d", y, z);
            // "%04d"
        System.out.println(s1);
        System.out.println(s2);
            // W:0005  X:0235
            // Y: 481  Z:  12
            // means to use 0 occupy the 4 digits, if empty
         
        String s1 = String.format("W:%-4d  X:%-4d", w, x);
            // left-justified
            // W:5     X:235 
            // Y: 481  Z:  12
         
Format Flag , - numeric values.// "%,.2f" round it into two decimal places

        int iVal = 1234567;
        String s1 = String.format("%,d", iVal);
            // 1,234,567 -  numeric values.
            
        double dVal =1234567.0d; // define first, then manipulate
        String s1 = String.format("%,.2f", dVal);
            // 1,234,567.00 - .2f rounding
            
 (http://www.java2s.com/Tutorials/Java/Java_Format/0080__Java_Format_Flags.htm)
 
    Flag	Description	//
    '-'	left justify. If there is no '-' flag, right justify.
    '#'	format in alternate form for the format specifier
    '+'	Add + sign to positive values. Applies only to numeric values.
    ' '	Add a leading space for positive values. Applies only to numeric values.
    '0'	Add zero padded. Applies only to numeric values.
    '('	Add parentheses for a negative number. It applies only to numeric values.
    '<'	Reuse the argument for the previous format specifier. It is mostly used in formatting dates and times.

Actual use of flag:

      ' ' - space holder
      
        int iPosVal = 123, iNegVal = -456;
        String s1 = String.format("%4d", iPosVal);
        String s2 = String.format("%4d", iNegVal);
        or
        String s1 = String.format("% d", iPosVal);
        String s2 = String.format("% d", iNegVal);
                //  123
                // -456     - space holder
        
      '+' - show the positive and negatrive
      
         String s1 = String.format("%+d", iPosVal);
         String s2 = String.format("%+d", iNegVal); 
                // +123
                // -456
                
       '%(d' - positive no; negative - ()
       
         String s1 = String.format("%(d", iPosVal);
         String s2 = String.format("%(d", iNegVal);  
                // 123
                // (456)  same size: %(4d or %( d
         
         
         String s1 = String.format("%d %d %d ", iPosVal, iNegVal, iNumber);
         String s2 = String.format("%3$d %1$d %2$d ", iPosVal, iNegVal, iNumber);

         System.out.println(s1);
         System.out.println(s2);   

Argument

        $ - order
        String s1 = String.format("%d %d %d ", iPosVal, iNegVal, iNumber);
        String s2 = String.format("%3$d %1$d %2$d ", iPosVal, iNegVal, iNumber);
        System.out.println(s1);
        System.out.println(s2);
                // 100 200 300 
                // 300 100 200 - %3$d %1$d %2$d: change the order here.
                
        < - copy the last value
        String s2 = String.format("%2$d %<d %1$d ", iPosVal, iNegVal, iNumber); 
                // 200 200 100 
                
        
