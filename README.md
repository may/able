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
    
5. Next time: launch the editor in one go (and auto-exit in one go):
    ```
    sbcl --eval "(ql:quickload \"able\")" --eval "(able::start)" --eval "(exit)"
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

10. Optional, extra credit: Make your REPL better!

    When you use SBCL (or most other Common Lisp implementations) outside of ABLE, try using [sbcli](https://github.com/hellerve/sbcli), which makes the REPL much nicer (up/down arrow keys work to recall what you've typed yesterday, for example).

# Features:

- REPL
- editor with matching parenthesis highlighting, simple syntax formatting, symbols completion
- menus with available commands:
  - manage buffers
  - talk to the Lisp: macroexpand, load file or buffer, compile file, lookup symbol on the CLHS
  - etc


Missing features:

- graphical interactive debugger (only native debugger available)
- saving REPL history across sessions

![image](https://github.com/may/able/assets/82888/5e0eadea-f874-46b5-8d9c-9b733ae6e689)


![](able1.png)

![](able2.png)
