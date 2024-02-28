//Java code to wish birthday at night.
import java.util.Scanner;
import java.awt.*;
import java.awt.event.*;
import java.awt.datatransfer.*;

public class TimeMessage 
{
    static void application(String msg) throws InterruptedException, AWTException
    {
        Scanner scr = new Scanner(System.in);
        StringSelection stringSelection = new StringSelection(msg);
        Clipboard clipboard = Toolkit.getDefaultToolkit().getSystemClipboard();
        clipboard.setContents(stringSelection, null);
        Robot robot = new Robot();
        robot.keyPress(KeyEvent.VK_CONTROL);
        robot.keyPress(KeyEvent.VK_V);
        Thread.sleep(100);
        robot.keyRelease(KeyEvent.VK_CONTROL);
        robot.keyRelease(KeyEvent.VK_V);
        Thread.sleep(500);
        robot.keyPress(KeyEvent.VK_ENTER);
        robot.keyRelease(KeyEvent.VK_ENTER);
        Thread.sleep(500);
        for(int i=1;i<=3;i++)
        {
            robot.keyPress(KeyEvent.VK_ALT);
            robot.keyPress(KeyEvent.VK_F4);
            Thread.sleep(500);
            robot.keyRelease(KeyEvent.VK_ALT);
            robot.keyRelease(KeyEvent.VK_F4);
            Thread.sleep(500);
        }
    }
    public static void main(String[] args) throws AWTException 
    {
       Scanner scanner = new Scanner(System.in);
        
       System.out.print("Enter the time (in HH:MM format): ");
       String inputTime = scanner.nextLine();
        
       System.out.print("Enter the message: ");
       String s = scanner.nextLine();

       String[] timeParts = inputTime.split(":");
       int hours = Integer.parseInt(timeParts[0]);
       int minutes = Integer.parseInt(timeParts[1]);
        

       java.util.Calendar calendar = java.util.Calendar.getInstance();
        

       calendar.set(java.util.Calendar.HOUR_OF_DAY, hours);
       calendar.set(java.util.Calendar.MINUTE, minutes);
        

       long currentTimeMillis = System.currentTimeMillis();
        
 
       long desiredTimeMillis = calendar.getTimeInMillis();
        
       long delayMillis = desiredTimeMillis - currentTimeMillis;
       delayMillis-=10000;
        if (delayMillis > 0) 
        {
            try 
            {
                Thread.sleep(delayMillis);
                System.out.println("Message: It's " + inputTime + " now!");
                application(s);
            } catch (InterruptedException e) 
            {
                e.printStackTrace();
            }
            
            scanner.close();
            
            return;
            
        } else 
        {
            System.out.println("Invalid time entered!");
            scanner.close();
            
            return;
            
       }
    }
}
