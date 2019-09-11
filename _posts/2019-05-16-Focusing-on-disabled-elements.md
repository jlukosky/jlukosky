---
layout: post
title: "Focusing on disabled elements: should disabled form elements receive focus?"
date: 2019-05-18
author: "John Lukosky"
category: accessibility
description: "An analysis of whether disabled form elements should be a web page's focus order"
tags: [disabled,focus,forms,screen reader]
ogimage: "https://jlukosky.github.io/assets/2019/05/horsesblurred.jpg"
---

![A sharply focused horse on a beach next to two blurred horses](/assets/2019/05/horsesblurred.jpg)

Updated 11 September 2019

A friend of mine insists that disabled form fields should be focusable. Their reasoning, as a blind person, is that it makes it easier to determine the contents of a form. We certainly don't want to hide anything.

Let's look at what makes a disabled form element special. According to [HTML5 4.13 Disabled elements](https://www.w3.org/TR/2014/REC-html5-20141028/disabled-elements.html), the following elements can be actually disabled using the disabled attribute:

- `button`
- `input`
- `select`
- `textarea`
- `optgroup`
- `option`
- `fieldset`

When these elements are disabled they cannot be focused. They will also match the :disabled pseudo-class.

Did you notice the `a` element isn't in the list of elements that can use the `disabled` attribute? If you're using anchors for buttons and other nonsense this is one more reason to reform your ways and follow semantics. Anchors don't support the disabled attribute.

Screen readers can read disabled elements by browsing the text with the arrow keys. As you can see from the allowed elements, `disabled` is only allowed on form controls. At times some may attempt to use it on the anchor element (`a`) but this will have no effect.

If you want to force focus, be aware **even tabindex="0" will not make disabled form elements focusable.**

Another consideration for these disabled elements is they are no longer subject to WCAG contrast requirements. They could be impossible to read and still be compliant. This stacks up oddly against what is happening for non-visual users. Non-visual users can read the disabled element's properties but this is not necessarily true for sighted users, particularly those with low vision.

## The verdict - disabled shouldn't focus

In this battle it seems clear that disabled elements should not be focusable given that:

1. HTML5 says disabled elements don't belong in the focus order.
2. Screen readers don't focus on form elements with the `disabled` attribute.
3. Screen readers (and sharp-eyed sighted folks) can still read the disabled element. It just won't receive focus.
4. Disabled elements aren't submitted. This further lessens the need to review the item.

## Other options to consider

So what to do with my friend who wants the disabled element to be more available? All is not lost, there are a couple of alternatives:

1. For `input` or `textarea` elements, making the element `read-only` instead of `disabled` will retain focusability.
2. If warranted, remove disabled elements instead of having them cluttering your form.
3. For a submit button, consider not using `disabled`. Instead, use an onclick informative message to alert the user to any errors or missed requirements.
