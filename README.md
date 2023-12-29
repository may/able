ABLE is a Common Lisp editor based on Tcl/Tk.

homepage: https://common-lisp.net/project/able/

# How to start it:
1. Install Tk if not present on your operating system (MacOS should include by default.):
    `apt install tk` (for Ubuntu Linux/Debian/Pop_OS)

2. Install Common Lisp if you haven't already:
    `apt install sbcl` (for Ubuntu Linux/Debian/PoP_OS)

3. Install QuickLisp if you haven't already, following the *official* instructions here: [https://www.quicklisp.org](https://www.quicklisp.org)
        Likely the instructions are the following:
               `curl -O https://beta.quicklisp.org/quicklisp.lisp`
               `sbcl --load quicklisp.lisp`
               `(quicklisp-quickstart:install)`
               `(ql:add-to-init-file)`

4. clone the repository where ASDF can find it (in ~/quicklisp/local-projects):
    `cd ~/quicklisp/local-projects`
    `git clone https://github.com/may/able.git`

5. launch the editor:
    `sbcl`
    `(ql:quickload "able")`
    `(able::start)`
   
7. Next time: launch the editor in one go:
`sbcl --eval "(ql:quickload \"able\")" --eval "(able::start)"`

# Features:

- REPL
- editor with matching parenthesis highlighting, simple syntax formatting, symbols completion
- menus with available commands:
  - manage buffers
  - talk to the Lisp: macroexpand, load file or buffer, compile file, lookup symbol on the CLHS
  - etc


Missing features:

- graphical interactive debugger (only native debugger available)

![](able1.png)

![](able2.png)
