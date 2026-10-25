cat > README.md << 'EOF'
# Inheritance: Blood Type Simulation

A C program that simulates how blood types are inherited across three generations of a family. This is the CS50x Problem Set 5 "Inheritance" assignment.

## How it works

Each person is a struct with two parent pointers and two alleles (A, B, or O).

- create_family(n) builds the family tree recursively. It makes one person, then calls itself twice with n - 1 to make that person's two parents. The base case is n == 1, the oldest generation, who get two random alleles and NULL parents. Everyone else gets one random allele from each parent.
- free_family(p) frees the tree recursively. The base case is p == NULL. It frees both parents first and the person last, because once a person is freed their parent pointers can no longer be read safely.

## Build and run

    make inheritance
    ./inheritance

Example output:

    Generation 0, blood type OB
        Generation 1, blood type OO
            Generation 2, blood type OA
            Generation 2, blood type OO
        Generation 1, blood type BB
            Generation 2, blood type AB
            Generation 2, blood type BO

The blood types change on every run because the alleles are random.

## Checking for memory leaks

    valgrind ./inheritance

The summary reports that all heap blocks were freed and there are 0 errors.

## Files

- inheritance.c: the full program
EOF
