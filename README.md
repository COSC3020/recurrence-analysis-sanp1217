[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=13123890&assignment_repo_type=AssignmentRepo)
# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Recurrence relation:
1 if n $\le$ 1
else 3T($\frac{n}{3}$ + $n^5$)

T(n) = 3T($\frac{n}{3}$) + $n^5$<br>
= $3 (3T(\frac{\frac{n}{3}}{3}) + (\frac{n}{3})^5) + n^5$ <br>
= $9T(\frac{n}{9}) + 3\frac{n^5}{3^5} + n^5$ <br>
= $3^iT(\frac{n}{3i}) + 100 + n^5$ Note: $3\frac{n^5}{3^5}$ is substituted by 100 since it will be some constant anyways. <br>
= $3^{\log_{3}(n)} T(\frac{n}{3^{\log_{3}(n)}}) + n^5$ for i = $\log_{3}{n}$ <br>
= n + $n^5$ $\in O(n^5)$





