ABLE is a Common Lisp editor based on Tcl/Tk.

homepage: https://common-lisp.net/project/able/

# Install & start it:
1. Install Tk if not present on your operating system:

   For Ubuntu Linux/Debian/Pop_OS:
   ```
   sudo apt install tk
   ```

   For MacOS:
   ```
   brew install tcl-tk
   ```

2. Install Common Lisp if you haven't already:
   
   For Ubuntu Linux/Debian/Pop_OS:
   ```
   sudo apt install sbcl
   ```

   For MacOS:
   ```
   brew install sbcl
   ```


3. Install QuickLisp if you haven't already, following the *official* instructions here: [https://www.quicklisp.org](https://www.quicklisp.org).

    Likely the instructions are the following:
    - ```
      curl -o /tmp/ql.lisp http://beta.quicklisp.org/quicklisp.lisp
      ```
    - ```
      sbcl --no-sysinit --no-userinit --load /tmp/ql.lisp \
       --eval '(quicklisp-quickstart:install :path "~/.quicklisp")' \
       --eval '(ql:add-to-init-file)' \
       --quit
      ```
      
4. clone the repository where ASDF can find it (in `~/.quicklisp/local-projects`):
    ```
    cd ~/.quicklisp/local-projects
    ```
    ```
    git clone https://github.com/may/able.git
    ```
    
5. Launch the editor in one go (and auto-exit in one go):
    ```
    sbcl --noinform --eval "(ql:quickload \"able\")" --eval "(able::start)" --eval "(exit)"
    ```

    If you recieve the error: `Couldn't execute "wish": No such file or directory` then you forgot to install TK. See step 1. In the meantime, press '3' or whichever number corrosponds to the `Exit SBCL` option.

   ![image](https://github.com/may/able/assets/82888/b95d66e1-d474-4603-8888-59a37566d149)

6. Next time: launch the editor much faster:

   Do this once:
   ```
   cd ~/.quicklisp/local-projects/able/
   ```
   ```
   sbcl --eval "(ql:quickload \"able\")" --eval "(sb-ext:save-lisp-and-die \"able.core\")"
   ```

   Do this _every_ time! (**much** faster!):

   ```
   sbcl --noinform --core ~/.quicklisp/local-projects/able/able.core --eval "(able::start)" --eval "(exit)"
   ```

7. To make it even easier on yourself, add this line to your `~/.zshrc` or `~.bashrc`:

   ```
   alias able='sbcl --noinform --core ~/.quicklisp/local-projects/able/able.core --eval "(able::start)" --eval "(exit)"'
   ```

   Now you can simply type `able` and be off to the races!

8. Optional, extra credit: Make your REPL *so* much better!

    Most default Common Lisp REPLs *suck* by default; no readline support, no history support, no nothing.

    But there's hope!

    When you use SBCL (or most other Common Lisp implementations) outside of ABLE, try using [sbcli](https://github.com/hellerve/sbcli), which makes the REPL much nicer (up/down arrow keys work to recall what you've typed yesterday, for example). 

    You can also save a transcript of your session, if needed.

    To install sbcli:
    1. Download a zip file from: https://github.com/hellerve/sbcli (click the big green Code button)  
    2. `unzip  unzip sbcli-master.zip `
    3. cd sbcli-master 
    4. sudo ./install.sh
    5. If you've followed the rest of this guide, your `quicklisp` will be in `~/.quicklisp` so you'll have to do this:
    6. `sudo nano /usr/local/bin/sbcli`
    7. Add a period before 'quicklisp' in line two:
       
    ![Screenshot from 2024-01-14 21-22-31](https://github.com/may/able/assets/82888/eafe3aa9-6ca1-4832-8b53-a510b5f9922d)


    9. Save the file with Ctrl-X to exit (answer Yes to saving the changes)
    10. Type `sbcli`
    11. Press `Ctrl-D` to exit `sbcli`.
    12. Bonus points, try the [micro](https://micro-editor.github.io/) editor.

    Other options: 
      * [linedit](https://github.com/sharplispers/linedit) (better tab completion, fewer features)
      * [cl-repl](https://github.com/lisp-maintainers/cl-repl)
      
# Features:

- REPL
- editor with matching parenthesis highlighting, simple syntax formatting, symbols completion
- menus with available commands:
  - manage buffers
  - talk to the Lisp: macroexpand, load file or buffer, compile file, lookup symbol on the CLHS
  - etc

# More screenshots

![image](https://github.com/may/able/assets/82888/5e0eadea-f874-46b5-8d9c-9b733ae6e689)


![](able1.png)

![](able2.png)

# Missing features:

- graphical interactive debugger (only native debugger available)
- saving REPL history across sessions
- git gutter
- line 80 highlight
- highlight current line
- highlight unmatched parens
- highlight *globals*
- highlight "strings"
- open recent files
- indentation on defun etc
- highlight TODO FIXME etc.
