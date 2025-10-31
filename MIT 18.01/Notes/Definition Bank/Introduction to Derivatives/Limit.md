# Defining Limit
- The limit of a function tells us what the $y$ value of a function is getting closer and closer to (approaching) as the $x$ value gets closer and closer to some specific number.
	- Note that the function does **not** need to reach that value or even be defined at that specific point for the limit to exist.
## Mathematical Notation
The concept of a limit for a function $f(x)$ as the input $x$ approaches a value $c$ is written as:
$$\lim_{x \to c} f(x) = L$$
Here:
- $\text{lim}$ is the abbreviation of limit.
- $x \to c$ represents "as $x$ approaches $c$". It represents the input ($x$) getting arbitrarily close to a specific number ($c$).
- $f(x)$ represents the [[Functions|function]] itself. - It represents the **output** value for a given input $x$.
- $L$ represents the limit value, which is the specific number that the output $y$ is approaching.
# $\epsilon-\delta$ (Epsilon - Delta) Definition
- The original equation $\lim_{x \to c} f(x) = L$ means that for *every* small number $\epsilon$ (which represents the desired closeness to $L$), there is a corresponding small positive number $\delta$ (which represents how close $x$ must be to $c$) such that *if* $x$ is within $\delta$ distance of $c$ (but not equal to $c$ itself), then the output, $f(x)$ is within $\epsilon$ distance of $L$.
## Mathematical Notation
$$\text{If } 0 < |x - c| < \delta \text{ then } |f(x) - L| < \epsilon$$
Here:
- **$|f(x) - L| < \epsilon$**: This means the distance between the output $f(x)$ and the limit $L$ is less than a tiny amount $\epsilon$. *The output is close to $L$.*
- **$0 < |x - c| < \delta$**: This means the distance between the input $x$ and the target $c$ is less than a tiny amount $\delta$. *The input is close to $c$.*
This definition makes sure that by making the input $x$ close to $c$ you can force the output $f(x)$ to be as close to $L$ as you want.
- The definition basically "legitimizes" the more informal definition above by putting it in more rigorous math terms by representing the idea of "as $x$ approaches $c$, $f(x)$ approaches $L$".
