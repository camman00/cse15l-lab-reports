# Original Post
<img width="202" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/ee54d1a5-878a-4372-b3c0-d4a889db580c">

Bug Description: I am creating a key logging program that is supposed to log each key individually.
Right now when I type one key it works perfectly but as soon as I type another key the program just
appends to the string that is presented. This is super annoying and I only want one key to show at a time.
I think this might have something to do with the way Java handles keyboard input events but I am still stuck.
Anytime I type more than once the symtpom occurs! Please help!
##### Posted By: ABC123
# TA Response
Hello ABC123 wowzers this is quite an unfortunate bug. Just to gather some background which operating system
are you using? Which specific Java components are you using to render the text? This might be a farcry
but I would recommend looking into whether or not you are using the right components for the job! Maybe
try using a different textual component! Also make sure that your events are working as intended and are in the correct spot!
##### Posted By: TA
# Student Response
<img width="526" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/68aec16b-bd7a-4b4e-966c-78ccf1f6705a">
<img width="198" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/48ecdd40-0b00-484c-9f6c-edcbcc90bcca">

Thank you so much your advice was SO helpful. It turns out I made a silly little error. Instead of adding my
KeyListener to the TextArea component I added it to the Frame. Since the Frame will not fire these key
events the TextArea was acting as intended and just putting in Text. To full proof this process I used
e.consume() to cancel the events and allow my custom action! Thank you so much!


# Post Resources
## Full Directory Struture
./labreport5:
KeyLogger$1.class       KeyLogger.class         start.bash
KeyLogger$2.class       KeyLogger.java
## Previous File (Before Fixing Bug)
KeyLogger.java
```Java
package labreport5;
import java.awt.Frame;
import java.awt.TextField;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
public class KeyLogger extends Frame {
    private TextField textArea;
    public KeyLogger() {
        setTitle("Key Logger");
        setSize(200, 200);
        setResizable(false);
        setUndecorated(true);
        textArea = new TextField();
        addKeyListener(new KeyListener() {
            @Override
            public void keyTyped(KeyEvent e) {
                e.consume();
            }
            @Override
            public void keyPressed(KeyEvent e) {
                e.consume();
                logKey("Key Pressed", e);
            }
            @Override
            public void keyReleased(KeyEvent e) {
                e.consume();
            }
            private void logKey(String eventType, KeyEvent e) {
                String logMessage = String.valueOf(e.getKeyChar());
                textArea.setText("");
                textArea.setText(logMessage);
            }
        });
        add(textArea);
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent windowEvent) {
                System.exit(0);
            }
        });
    }
    public static void main(String[] args) {
        KeyLogger keyLoggerAWT = new KeyLogger();
        keyLoggerAWT.setVisible(true);
    }
}
```
start.bash
```bash
if [ ! -f "KeyLogger.java" ]; then
    javac "KeyLogger.java"
fi
cd ..
java labreport5.KeyLogger
```
## Command To Trigger Bug
`bash start.bash`
As soon as the window opens pressing mutiple keys should show the symptom!
## Fixing The Bug
To fix the bug we need to change this one specific line
```Java
textArea.addKeyListener(new KeyListener() {
```
Before the event listener was being added to the outside element which is the Frame. This is not what we want -
because the outter most element does not have anywhere to take input. We want the textArea to have this key listener and this
change fixes the bug!
# Part 2 - Reflection
I really enjoyed working with Vim. This was something that I had no previously worked with and I found it to be
really interesting. I also learned more about JSON payloads from one of my tutors. I asked him about passing
large bulks of information through a query. He said that query's have limits and that a JSON payload would be
the best way to send and recieve this information. I also learned more about ls command. Specifically my new
favorite flag is -R which prints out everything in all its sub directories recursively and printing it in a very nice format.
