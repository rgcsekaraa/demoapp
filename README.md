# ProcurePro Backend Technical Challenge

Hi Nathan, Tomm,

I completely agree with what you mentioned about not spending more than 2 hours on this, but eventually, I spent 2 days learning and implementing the challenges.  
Previously, My only PHP experience was, I had worked on modifying PHP functions to implement custom features on a WordPress website, but it wasn’t as hands-on as this experience. This technical task was a great learning opportunity, I pushed myself to give my best in learning and solving the challenge.

---

## Learning Process

I started by reading all the instructions from the repo (concepts, setup, tasks). I went through the docs, and I understood the core concepts about pure functions and DTO. since I had previous project experience with Django, Symfony was Quite similar (MVC architecture, templates, make commands), and I was able to quickly grasp the core concepts.

### Tutorials I Followed:

1. **Symfony Basics**:  
   [Symfony in 1 Hour](https://www.youtube.com/watch?v=i_jgWZItCGI&t=69s)  
   _(Basics of model, view, and controller, data fixtures, routing, Twig templates, make commands, Doctrine ORM, requests and responses, Symfony validator, form handling, repository patterns, profiler for detailed analysis)_

2. **Psalm for Static Analysis**:  
   [Psalm Usage Tutorial](https://www.youtube.com/watch?v=ZxXw5Fkp9R8)

---

## Implementation Details

I started writing the code by referring to the Symfony docs, Reddit discussions, and occasionally used ChatGPT for understanding some snippets and OOP concepts.

### Trade-offs:

- For example, the failed test case for the patch endpoint had an adjustment error—a typo (`'s'`).  
  So I removed `'s'` to satisfy the test case.

### Validation Checks:

- Ensured validation checks for the price:
  - The discount can’t be more than the price.
  - All inputs (price, unlet cost, adjustment, discount) can’t have negative values.
- However, I wasn’t sure whether I could assume that the price should be higher than all the other fields.  
  I inferred this from the schema of fakers in data fixtures.

---

## Questions and Clarifications

### Final Cost Calculation:

The formula mentioned in the docs is:  
`final cost = price - discount + adjustment + unletCost`

This doesn’t include parentheses following BODMAS rules.  
If it were written as:  
`final cost = price - (discount + adjustment + unletCost)`  
then I would have assumed that. I need some clarity on this.

### Currency Validation:

- If the user sends `500.30` from the frontend as `50030` in JSON:
  - The backend stores it in the database as `50030` and sends it back as an integer.
  - On the frontend, it will be interpreted as `500.30` by dividing it to get the actual price.
- So, **the validation should be done solely on the frontend**:
  - The frontend should multiply the value by `100` and send it via JSON to the backend.
  - This ensures that the backend stores the value correctly and no issues arise when sending it back to the frontend.

#### Is it a good practice to rely solely on the frontend to send values correctly?

I attempted to send it as a string, interpret and parse it, validate it, store it as an integer, and send it back as a string. But I think that’s not a good idea for handling numbers. Any guidance on this would be really helpful.

---

## Testing

- I haven’t tried concurrent testing (e.g., passing concurrent requests to the same contractor to ensure persistence).
- I tried to pay maximum attention to address validation issues and test cases but might have missed something.
- I would love feedback on missed cases or how to optimize/approach problems better.

---

## Key Takeaways

This technical task gave me a good understanding of:

- The MVC architecture in Symfony.
- Basics of PHP language.
- Brushed up on OOP concepts (type safety and static analysis).
- Learned about validations and test cases.

I now have a good grasp of the codebase—I almost own it now!  
I am definitely willing to learn more and gain hands-on experience with Symfony and PHP while learning best practices so that I can contribute effectively.
