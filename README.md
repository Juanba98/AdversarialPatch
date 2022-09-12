# Adversarial Patch attack (https://arxiv.org/abs/1712.09665).

We replace a part of a image with a patch. This patch must be masked to allow it to take any shape (in this aproach just a circle), then train this patch over a data set of images, applying a random translation, scaling and rotation on it for every image, and optimizing using gradient descent.

Given a image $x \in \mathbb{R}^{w \times h \times c}$, patch $p$, patch location $l$, and patch trasnformation $t$, we define a *patch aplication operator*

$$A(p,x,l,t)$$

That apply the transformation $t$ to the patch $p$, and then applies the transformed partch $p$ to the image $x$ at location $l$

To obtain the trained patch $\hat{p}$ (Variant of Expectation over Transformation (EOT))

$$\hat{p} = arg \max_{p} \mathbb{E}_{x \sim X,t\sim T,l\sim L} [logPr(\hat{y}|A(p,x,l,t))]$$

* $X$ is a training set of images
* $T$ is a distribution over transformations of the patch
* $L$ is a distribution over locations in the image 



##Referential implementation:
- https://github.com/cleverhans-lab/cleverhans/blob/master/cleverhans_v3.1.0/examples/adversarial_patch/AdversarialPatch.ipynb
- https://github.com/jhayes14/adversarial-patch
- https://github.com/A-LinCui/Adversarial_Patch_Attack
