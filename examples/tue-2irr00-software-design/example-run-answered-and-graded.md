# Example Run: Design Patterns and Refactoring

Status: completed example

This is example-only. The prompts are altered practice questions, not copied source exam questions.

Source frame:
- Course context: TU/e 2IRR00 Software Design.
- Source documents: local-only lecture slides and rubric notes.
- Source map: `example-topic-source-map.md`
- Ledger: `example-ledger.md`

## Topic 1: Strategy vs Template Method

Prompt:

A media player supports different subtitle synchronization algorithms. The team wants users to switch algorithms at runtime. Another part of the system has a fixed import pipeline where subclasses may customize one parsing step while the overall sequence must stay fixed.

Which pattern fits each case, and why?

### Answer

Use Strategy for the subtitle synchronization algorithms because the behavior should be interchangeable at runtime through composition. The player can hold a synchronization strategy interface and swap concrete strategies.

Use Template Method for the import pipeline because the algorithm skeleton should remain fixed in a superclass while subclasses override specific steps.

### Grading Notes

Score: 4/4.

- Correctly chose Strategy for runtime interchangeable behavior.
- Correctly used composition/interface language.
- Correctly chose Template Method for a fixed algorithm skeleton.
- Correctly described subclass customization of individual steps.

## Topic 2: Refactoring and Code Smells

Prompt:

A class named `ReportManager` validates input, queries storage, formats PDF output, sends email, and logs analytics. A teammate proposes splitting it into smaller collaborators and says this is a bug fix.

Identify the likely smell and explain whether the proposed change is refactoring.

### Answer

The likely smell is a large class or god class because it has too many responsibilities. Splitting it into smaller collaborators can be refactoring if the external behavior stays the same. It is not a bug fix by itself unless it changes incorrect behavior.

### Grading Notes

Score: 5/5.

- Correctly identified large class/god class.
- Explained the responsibility problem.
- Correctly defined refactoring as internal restructuring.
- Stated that external behavior must stay unchanged.
- Distinguished refactoring from a bug fix.

## Run Summary

Total: 9/9.

Ledger update:
- Design-pattern comparison improves toward test-stage once repeated blind.
- Refactoring and code smells can move from `open` to `test_stage` after a later full-scoring real run.
