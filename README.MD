# ESEP Grade Calculator

A small Go library that calculates a student's final letter grade from three kinds of grades:
assignments, exams, and essays. Each kind is averaged, the averages are combined using weights,
and the weighted number is converted to a letter grade.

## Requirements

- Go 1.24 or newer (check with `go version`). Install from https://go.dev/dl/ or with `brew install go` on macOS.
- Git

## Project layout

```
esep-grade-calculator/
├── README.MD
└── grade-calculator/
    ├── go.mod                     # Go module definition (module name + Go version)
    ├── grade_calculator.go        # The library code
    └── grade_calculator_test.go   # Unit tests
```

## Setup

```
git clone https://github.com/<your-username>/esep-grade-calculator.git
cd esep-grade-calculator/grade-calculator
```

Note: the folder is `grade-calculator` (with a dash), not `grade_calculator`.

## How to use the library

```go
calc := NewGradeCalculator()
calc.AddGrade("open source assignment", 100, Assignment)
calc.AddGrade("exam 1", 95, Exam)
calc.AddGrade("essay on ai ethics", 91, Essay)
letter := calc.GetFinalGrade() // returns "A", "B", "C", "D", or "F"
```

- `NewGradeCalculator()` creates an empty calculator.
- `AddGrade(name, grade, type)` adds one grade. `type` is `Assignment`, `Exam`, or `Essay`.
- `GetFinalGrade()` returns the letter grade.

## Run the unit tests

From inside the `grade-calculator` folder:

```
go test ./...          # run all tests
go test -v ./...       # run all tests and list each one with PASS/FAIL
```

## Run the tests with code coverage

```
go test -cover ./...                                  # print coverage percentage
go test -coverprofile=coverage.out ./...              # save coverage data to a file
go tool cover -func=coverage.out                      # coverage per function
go tool cover -html=coverage.out                      # open a color-coded report in your browser
```
