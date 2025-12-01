# ***Part A: The Critical Distinction***
1. Write short, honest answers to these questions:
    - **How have you used AI for coding so far?**
    I have used AI in some parts of my coding so far, but most of the time it is to learn how to do things I don’t know. So I ask the AI to show me what to do and then teach me why and how it’s working.

    - **Do you usually try problems yourself first?**
    Yes, when I have to solve a problem first I try to break it down to smaller problems and solve them one by one.

    - **Can you explain the code you've submitted without AI's help?**
    Yes, I can, because even if I’ve had a part of my code AI generated I always ask the why and how the AI did it. So I can understand and learn ways of coding that evade my grasp.

    - **What would happen if AI was unavailable during an exam or job test?**
    Nothing. I would try to solve my problem part by part till everything is sorted.

2. Identify your current pattern:

    Learner B: I utilize AI so I can access knowledge that would take me forever to find it.

3. When I started the program I had knowledge in coding, but it was mainly theoretical like algorithms and problem solving. In my current state I can firmly say that with practice and collaboration with peers and with correct usage of the AI I have learned ways of coding that I didn’t know before. The type of learner I would like to become is already set from the very first interactions I had within the program. I want to use AI in order to learn or deep research a project and then code it myself. Last but not least I know that even using AI we must never forget our peers. Their insight might enlighten us in ways we could think of. AI is a tool, not a peer.


# ***Part B: The Wrong Way vs. The Right Way***
## **Step 1: Attempt independently**
Before the pseudocode we must say a couple of things about the functionality of the code. The function must return a boolean value according to the result, TRUE if the string is a palindrome / FALSE if the string is not a palindrome. We must begin by taking a string argument and “break” it in an array where we have the individual letters, during this task we must also remove spaces and convert capital letters to lowercase to avoid false results. Then we start from both ends and proceed towards the middle of the slice checking every time the two letters if they are different. If we come across different letters then the function must return FALSE, since it’s not a palindrome. If the repetition process ends and we didn’t come across different letters then the string is a palindrome and the function should return TRUE.



**Pseudocode:**

    function isItPalindrome(str):
    cleaned ← empty string
    FOR each char in str:
        IF char is an alphabet letter:
            cleaned ← cleaned + lowercase(char)
    left  ← 0
    right ← length(cleaned) - 1
    WHILE left < right:
        IF cleaned[left] <> cleaned[right]:
            RETURN false
        left  ← left + 1
        right ← right - 1
    RETURN true

**Python implementation:**

    def is_palindrome(text):
        cleaned = ""

    # Keep only alphabet letters and convert them to lowercase
    for char in text:
        if char.isalpha():
            cleaned += char.lower()

    # Convert the string into a list of characters
    chars = list(cleaned)

    left = 0 # Set the position of the first letter
    right = len(chars) - 1 # Set the position of the last letter

    while left < right:
        if chars[left] != chars[right]:
            return False  # Different letters = It is not a palindrome

        left += 1
        right -= 1

    return True  # No mismatches = It is a palindrome

## *Step 2: Strategic AI use*
- What's the time complexity?

    Your function has three phases:

    1.  Cleaning loop
        -   `cleaned += char.lower()` creates a new string each time →
            O(n²) overall.
    2.  Convert to list
        -   `list(cleaned)` → O(n).
    3.  Two‑pointer comparison
        -   Runs in O(n).

    **Overall time complexity:** O(n²)

    **Space complexity:** O(n)


- What edge cases might I miss?

    -   Unicode normalization issues (`é` vs `e` + accent)
    -   Non-Latin alphabets
    -   Characters with special casing (e.g., German **ß**)
    -   Apostrophes in words
    -   Strings with no alphabetic characters (`"123!!"` becomes empty →
        palindrome)
    -   Combining characters vs precomposed characters


- Alternatives and trade-offs?

    1. **Two-pointer method (my approach)**

        - How it works:
        Compare characters from both ends moving toward the center.

        - Time complexity: O(n)

        - Space complexity: O(n) because you build cleaned and chars.

        - **Pros:**

            - Simple, readable

            - Efficient for checking palindromes

            - Stops early on mismatch

        - **Cons:**

            - String concatenation (cleaned += ...) is inefficient → O(n²) preprocessing

            - Requires extra memory for chars

            - Doesn’t handle Unicode normalization issues

            - Ignores only non-alphabetic characters (not digits, accents, etc.)


    2. **Built-in reverse comparison**

        ``` python
        cleaned == cleaned[::-1]
        ```

        - **Pros:**

            - Very short

            - Still O(n)

        - **Cons:**

            - Creates a copy of the reversed string → extra memory

            - Cannot stop early on mismatch


    3. **Use a list instead of repeated string concatenation**

        ``` python
        cleaned_chars = []
        cleaned_chars.append(char.lower())
        ```

        - **Pros:**

            - Cleaning becomes O(n) instead of O(n²)

            - Faster on long inputs

        - **Cons:**

            - Slightly less “beginner-friendly” than `+=`
            - Still allocates a full cleaned list     


    4. **Streaming two-pointer approach (no extra memory)**

        More advanced:


        Skip punctuation while moving pointers rather than building a cleaned string.
        - **Pros:**

            - True O(1) extra space

            - Very fast

        - **Cons:**

            - More complex and harder to read
            - Requires careful handling of indexes and character checks  


    5. **Regular-expression cleaning**

        ``` python
        import re
        cleaned = re.sub(r'[^a-z]', '', text.lower())
        ```

        - **Pros:**

            - Clear intent

            - Good performance for large text

        - **Cons:**

            - Requires regex knowledge
            - Extra overhead of the regex engine            


- How does your code perform on very long strings?

    According to AI my code has two performance characteristics:
    1. **Cleaning step: inefficient (O(n²))**

        This line is the issue:
        ``` python
        cleaned += char.lower()
        ```
        For each character, Python builds a new string, so the total cost becomes:
        `1 + 2 + 3 + ... + n  =  O(n²)`

        **Impact:**

        - On a 1,000-character string, still fast.

        - On a 1,000,000-character string, performance becomes very slow.

        - Memory usage also grows because you repeatedly create intermediate string objects.

    2. **Palindrome check step: efficient (O(n))**

        The two-pointer loop:
        ``` python
        while left < right:
        ```

        Performs at most *n/2* comparisons → **O(n)**.

        **This part scales very well, even for millions of characters.**

    ***In a few words AI has the following opinion:***
     
    - Your current code is perfectly fine for:
           
        - Short phrases
          
        - Normal text input
           
        - Typical interview or exercise cases

    - But for very long strings (hundreds of thousands or millions):
           
        - The cleaning step becomes too slow.
           
        - Memory usage becomes significant.
           
        - A list-based or streaming approach works much better.


## Step 3 - Reflection
- Through testing I've learned that it's easy to miss some cases like the spacing or capital letters not being equal to lowercase letters, thus providing a logical error.

- After using AI I've learned two things:
    1. Strings are already indexable in Python, so I don’t need chars = list(text) 
    2. You can save a lot of processing time.
    3. My code was based in English texts, but it is better to use Unicode so it can be applied to other languages as well.

- Yes, I'm able to create similar functions and keep in mind the cases I missed or the fact that the appliance of my code could have a broader spectrum if I want to, or need to, go to that direction.



# *Part C: Testing Your Understanding*

Modifications for **ignoring spaces and punctuation** and **being case-insensitive** are already in my code so the only reason to modify it further is to return the position where the string stops being a palindrome (if not a palindrome).

**Pseudocode:**

    function isItPalindrome(str):
    cleaned ← empty string
    FOR each char in str:
        IF char is an alphabet letter:
            cleaned ← cleaned + lowercase(char)
    left  ← 0
    right ← length(cleaned) - 1
    WHILE left < right:
        IF cleaned[left] <> cleaned[right]:
            RETURN false, left, right  
        left  ← left + 1
        right ← right - 1
    RETURN true, -1, -1

**Python implementation:**

``` python
def is_palindrome(text):
    cleaned = ""

for char in text:
    if char.isalpha():
        cleaned += char.lower()

chars = list(cleaned)

left = 0 
right = len(chars) - 1 

while left < right:
    if chars[left] != chars[right]:
        return False, left, right # Returns the boolean and the index of mismatch

    left += 1
    right -= 1

return True, -1, -1 # We need the -1 otherwise there would be a problem with the return values
```

***I used AI strategically by asking the following questions:***

**-Did I miss any edge cases?**

1. **Unicode letters and accents**

    `.isalpha()` treats many characters as letters, including:

    - `"é"`, `"ü"`, `"ß"`, `"ø"`

    - Greek, Cyrillic, Arabic, etc.

    But some composed and decomposed Unicode characters compare differently:

    Example:

    - `"é"` → could be `U+00E9`

    - or `"e"` + combining accent → `U+0065` + `U+0301`

    These may not match unless you normalize Unicode:
        
    ``` python
        import unicodedata
        text = unicodedata.normalize("NFC", text)
    ```

2. **Non-alphabetic but alphanumeric characters**

    Since you use `isalpha()`, you ignore digits:

    - `"12321"` → becomes `""` → returns `(True, -1, -1)`

    - `"1a1"` → becomes `"aa"` → returns palindrome even though the original string isn’t

    This may or may not be desired.

3. Strings that clean down to empty

    Examples:

    - `"!!!???"`

    - `"12345"`

    - `"-- --"`

    These become:

    ``` python
    cleaned = ""
    ```

    Your function returns `(True, -1, -1)`.

    This is logically fine but worth noting as an edge case.

4. Very long strings

    Your comparison logic handles them, but preprocessing (`cleaned += ...`) behaves badly (details below).

**-How could the function be more efficient?**

    Use a list to build cleaned characters:

``` python
cleaned_chars = []
for char in text:
    if char.isalpha():
        cleaned_chars.append(char.lower())

chars = cleaned_chars
```

- This reduces preprocessing to O(n)
- Overall function becomes a true O(n) palindrome checker
- No behavioral changes — logic stays identical
