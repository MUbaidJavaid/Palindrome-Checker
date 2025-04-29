PDA Palindrome Validator

   A web-based visualization tool demonstrating how a Pushdown Automaton (PDA) validates palindromes using stack operations.


Features

   Interactive PDA Simulation:

        Visualizes stack operations (push/pop) with animations

        Shows state transitions in real-time

        Displays input tape with current position pointer

   Comprehensive Input Handling:

        Case-insensitive comparison

        Automatically ignores non-alphanumeric characters

        Handles both even and odd-length palindromes

   Educational Components:

        Detailed theory section explaining PDA concepts

        Formal definition of the implemented PDA

        Step-by-step operation log

        Example test cases


How to Use

    Enter a string in the input field (e.g., "racecar", "A man, a plan...")


    Choose interaction mode:

        Click "Validate" to run full automatic simulation

        Click "Step Through" to manually advance each operation


    View the visualization:

        Stack operations (push/pop animations)

        Current PDA state (highlighted in diagram)

        Input tape with position pointer


    See the final result (Accepted/Rejected)

    Use "Reset" to start over with a new string      

Theory Behind the Implementation

    Why PDAs for Palindromes?

        Finite Automata cannot recognize palindromes because they lack memory. PDAs extend FAs with a stack, allowing them to:

            Remember the first half of the string (by pushing to stack)

            Compare with the second half (by popping from stack)


    Formal PDA Definition

        States (Q): {q₀ (push phase), q₁ (compare phase), q₂ (accept state)}

        Input Alphabet (Σ): All alphanumeric characters

        Stack Alphabet (Γ): Σ ∪ { = stack bottom marker)

        Transition Function (δ):

            q₀ → q₀: a,ε→a (push a)

            q₀ → q₁: ε,ε→ε (switch to compare)

            q₁ → q₁: a,a→ε (pop and match)

            q₁ → q₂: ε,$→ε (accept)

        Start State: q₀

        Accept State: q₂

Algorithm Steps

    Input Cleaning:

        Convert to lowercase

        Remove non-alphanumeric characters

    Push Phase (q₀):

        Push first half of characters onto stack

        For odd lengths: (length/2) characters

    Compare Phase (q₁):

        Skip middle character if length is odd

    For each remaining character:

        Pop from stack

        Compare with current input character

        If mismatch → reject

    Acceptance (q₂):

        After processing all characters:

           If stack only contains $ → accept

           Otherwise → reject

Example Test Cases

                Input	Cleaned Version	Valid Palindrome?

                "racecar"	"racecar"	✅ Yes
                "A man, a plan, a canal: Panama"	"amanaplanacanalpanama"	✅ Yes
                "abba"	"abba"	✅ Yes
                "abcba"	"abcba"	✅ Yes
                "hello"	"hello"	❌ No
                "abc123"	"abc123"	❌ No



Technical Implementation

        Frontend: HTML, Tailwind CSS, Vanilla JavaScript

        No Dependencies: Pure client-side implementation

        Animations: CSS transitions and keyframes

        Responsive Design: Works on mobile and desktop


Future Enhancements

        Support for more complex palindrome types

        Additional PDA examples (e.g., balanced parentheses)

        Exportable operation history

        User-adjustable animation speed

        Multiple PDA visualization modes