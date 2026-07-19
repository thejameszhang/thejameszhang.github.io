---
layout: about
title: About
permalink: /
# subtitle: <a href='#'>Affiliations</a>. Address. Contacts. Motto. Etc.

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  # more_info: >
  #   # <p>555 your office number</p>
  #   # <p>123 your address street</p>
  #   # <p>Your City, State 12345</p>

news: false # includes a list of news items
selected_papers: false # includes a list of papers marked as "selected={true}" (off: publications hidden, James Jul 2026)
social: true # includes social icons at the bottom of the page
---

## Bio

I am a Pre-Doctoral Research Fellow at the [Yale School of Management](https://som.yale.edu/) and [Tobin Center for Economic Policy](https://tobin.yale.edu/), where I am fortunate to be advised by Professor [Bryan Kelly](https://www.bryankellyacademic.org/). Prior to joining Yale, I received my B.S. in Computer Science and Mathematics from the [University of Maryland, College Park](https://www.umd.edu/), where I was advised by Professor [Serhiy Kozak](https://serhiykozak.com/).

## Research

Much of my work sits at the intersection of machine learning and financial markets. These days, I focus on large language models and how automated text annotations can shed light on key questions in asset pricing and macroeconomics. Before that, at Maryland, I focused on empirical asset pricing, including factor models and kernel methods. More broadly, I'm also drawn to global macro, commodity markets, and random matrix theory.

## Prediction Markets

Away from research, I like putting ideas to work in live markets. Right now that means prediction markets like Kalshi. I run a few high(er)-frequency market-making algorithms in Rust that trade WTI crude oil, Bitcoin, NBA and MLB games, and some other markets. The applied side (pricing, risk, and the mess of real order flow) is where I have the most fun, and, so far at least, it's even made a little money. My code is private, but I'm always happy to chat about market making, prediction markets, or applied problems in finance and tech more broadly. If any of that overlaps with what you're working on, [reach out](mailto:james.y.zhang@yale.edu).

<style>
:target { scroll-margin-top: 6rem; }
.cv-btn {
  display: inline-flex;
  align-items: center;
  gap: .45em;
  padding: .5em 1em;
  border: 1px solid var(--global-theme-color);
  border-radius: 8px;
  color: var(--global-theme-color);
  text-decoration: none;
  font-size: .95em;
  transition: background .15s ease, color .15s ease;
}
.cv-btn:hover { background: var(--global-theme-color); color: #fff; }

/* Home page: calmer heading scale + more breathing room */
#about .post-title { font-size: 2rem; margin-bottom: 1.5rem; }
#about article h2 {
  font-size: 1.45rem;
  font-weight: 400;
  margin-top: 3rem;
  margin-bottom: 0.65rem;
}
#about article p { line-height: 1.7; margin-bottom: 1.15rem; }
#about article ul { margin-top: 0.6rem; }
#about article li { margin-bottom: 1.2rem; line-height: 1.65; }
</style>

## Data & Code {#data-code}

Selected research code and datasets.

- **Global Macroeconomic Data**<br>
  The macro counterpart to the [Global Factor Data](https://jkpfactors.com/) (Jensen, Kelly, and Pedersen 2023). It includes eight datasets of global futures returns using data from LSEG Tick History, LSEG Datastream, and Compustat. Joint work with [Bryan Kelly](https://www.bryankellyacademic.org/) and Faheem Almas.<br>
  Documentation *(coming soon)* · Data *(coming soon)* · [Code](https://github.com/thejameszhang/futures){:target="_blank"}

- **Tensor Factor Models**<br>
  An Orthogonal PARAFAC tensor decomposition for latent three-dimensional factor models of returns across time, lags, and the cross-section, joint work with [Serhiy Kozak](https://serhiykozak.com/) and [Markus Pelger](https://mpelger.people.stanford.edu/). Estimation is cast as an alternating-optimization problem and solved with Alternating Least Squares and the Alternating Direction Method of Multipliers.<br>
  [Code](https://github.com/thejameszhang/tensor-factor-models){:target="_blank"}

- **Kernel Trick for the Cross-Section**<br>
  A kernel-methods model of the cross-section of returns, with [Serhiy Kozak](https://serhiykozak.com/). The custom Gaussian kernel operation is written in C++/CUDA and registered as a differentiable JAX primitive.<br>
  [Code](https://github.com/thejameszhang/kernel-trick){:target="_blank"}

<div style="display: flex; align-items: center; gap: 1rem; margin-top: 2rem;">
<h2 id="cv" style="margin: 0;">CV</h2>
<a class="cv-btn" href="{{ '/assets/pdf/james-zhang-resume.pdf' | relative_url }}" target="_blank" role="button"><i class="ti ti-download"></i> View my CV (PDF)</a>
</div>
