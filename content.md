# Debugging Tips
Debugging is an essential skill for any programmer. It involves identifying and fixing errors or bugs in your code. This lesson will guide you through some effective debugging techniques in Ruby, focusing on methods that beginners can easily adopt.

## Rubber Duck Debugging 🦆
Sometimes when you're stuck on a problem, the solution isn't immediately clear. One technique many programmers use is to talk through the problem as if they're explaining it to someone else. This method is affectionately called "rubber ducking."

### What is Rubber Duck Debugging?
The term "rubber duck debugging" comes from a story where a programmer carried around a rubber duck and would debug their code by explaining it, line by line, to the duck. The key idea is that by vocalizing the problem and attempting to explain it in simpler terms, you often see the issue from a new angle or realize something you hadn’t previously considered.

Instead of relying on others for help, try using an inanimate object or even a pet as your audience. Whether it’s your dog, cat, or an actual rubber duck, the act of explaining your problem out loud can lead you to the solution.

### Why is "rubber duck debugging" useful?
- It forces you to articulate your thoughts, which can reveal new insights.
- It helps build independence in problem-solving.
- It provides a non-judgmental "listener" that allows you to explore different aspects of the problem.

<!-- here to break up list/quiz -->

- What is the main benefit of "rubber duck debugging"?
- It provides a new angle on a problem by forcing you to articulate it clearly.
  - Correct! You'll be surprised how often talking to yourself helps you understand a problem better.
- It helps you ask for help from others.
  - Not quite. Remember, this method is about independence.
- It allows you to see the problem from the duck's perspective.
  - Not quite. The duck itself isn’t the focus, but rather the process of explaining.
{: .choose_best #rubber_duck title="The Benefit of Rubber Duck Debugging" points="1" answer="1" }

## Practical Debugging Tips

### 1. Use `puts` or `p` Statements
One of the simplest and most effective ways to debug is by using `puts` or `p` statements to print out values and inspect the flow of your code. These statements will display information in the console, allowing you to track the state of variables or the progress of loops and conditionals.

#### Example:
```ruby
x = 10
y = 20
puts "x: #{x}, y: #{y}"
```

This will output:

```
x: 10, y: 20
```

I highly recommend adding `puts` and `p` statements throughout your code and reading logs to follow the flow of your code.

### 2. Check the Logs
When you're running your Ruby or Sinatra application, errors and important events are often logged in the console or log files. Checking these logs can provide valuable insights into what might be going wrong.

#### 3. Always read the full error message.
Look for the stack trace, which tells you where the error occurred. A stack trace is a report that Ruby generates when an error occurs. It shows the sequence of function calls that led to the error, helping you identify exactly where and why something went wrong.

Example:

```ruby
def divide(a, b)
  a / b
end

divide(10, 0)
```

This code will produce a ZeroDivisionError, and the stack trace will show you where the error occurred. Make sure to look for line numbers. In this case, line 2 (where the ZeroDivisionError was raised) and line 5 (where the divide method is called).

```bash
app.rb:2:in `/': divided by 0 (ZeroDivisionError)
        from app.rb:2:in `divide'
        from app.rb:5:in `<main>'
```

- What should you look at first when a Ruby error occurs?
- The stack trace.
  - Correct! The stack trace helps you identify where the error occurred.
- The first line of code.
  - Not quite. The stack trace gives a more specific location of the error.
- The output of your puts statements.
  - Not quite. While puts can help, the stack trace is more specific.
{: .choose_best #stack_trace title="Reading the Stack Trace" points="1" answer="1" }

### 4. Use `binding.irb`
For more complex debugging, you can use `binding.irb` to drop into an interactive Ruby shell (IRB) right in the middle of your program. This allows you to inspect variables, run methods, and explore the state of your program at the exact point where you inserted `binding.irb`.

Example:

```ruby
def calculate_total(price, tax)
  binding.irb  # Debugging starts here
  total = price + tax
end

calculate_total(100, 20)
```

When you run this code, it will pause execution at `binding.irb`, allowing you to interactively debug.

```
% ruby app.rb

From: app.rb @ line 2 :

    1: def calculate_total(price, tax)
 => 2:   binding.irb  # Debugging starts here
    3:   total = price + tax
    4: end
    5: 
    6: calculate_total(100, 20)

irb(main):001> 
```

This allows us to print out the values of our variables at this specific point in execution.

```
irb(main):001> price
=> 100
irb(main):002> tax
=> 20
irb(main):003> 
```

You can use the `exit` command to continue execution.

```
irb(main):003> exit
```

- What does `binding.irb` allow you to do?
- Drop into an interactive Ruby shell to inspect and debug your program.
  - Correct! `binding.irb` is a powerful tool for real-time debugging.
- Print out variables in the console.
  - Not quite. While you can print variables, `binding.irb` does much more.
- Stop the program from running.
  - Not quite. It pauses execution but lets you interact with the code.
{: .choose_best #binding_irb title="Using binding.irb" points="1" answer="1" }

## Summary
Debugging is about understanding what's going wrong in your code and finding ways to fix it. By using techniques like rubber duck debugging, puts and p statements, checking logs, reading stack traces, and using binding.irb, you can become more efficient at finding and fixing bugs in your Ruby programs.

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken title="Time taken" points="1" answer="any" }

## Resources

- [Rubber Duck Debugging: The Psychology of How it Works](https://www.thoughtfulcode.com/rubber-duck-debugging-psychology/)
