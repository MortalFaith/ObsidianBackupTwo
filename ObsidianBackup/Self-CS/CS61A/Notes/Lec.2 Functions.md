# using f(x) to express all the expressions

to do this, we need to: 
1. read nested expressions
2. give values
3. create function by giving values or define

f(x) gets revaluated every time its called.


![[76DE835D0016097315BBB083F58E22EB.png]]

remember: max may not be max!

# How to call user-defined functions
1. add a local frame (our function) followed by global frame
3. Bind the function's formal parameters to its arguments in that frame
4. excute

![[888D0B64BB85245F1BB470E4195A5B07.png]]

**Most important:**

environment made by a sequence of frames, which is the sequence of frames.
frames bind names and values.