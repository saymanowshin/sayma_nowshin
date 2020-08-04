# 1. Background of Calcium Imaging data

Auditory communication in natural acoustic environments requires listeners to discriminate sounds based on behavioral meaning, but it is unclear how task-related information about target vs. non-target sounds is encoded in primary auditory cortex (A1). Thus, we trained mice to perform a go/no-go pure-tone frequency discrimination task while we captured the activity of neuronal populations with in vivo 2-photon (2P) Ca2+ imaging during task performance. We found on the single-cell level that the amplitude of responses was modulated by behavioral choice (hit, misses, false alarms and correct rejections). Pure-tone responsiveness in A1 during correct behavioral choices (hits and correct rejections) had a small negative gain. A small positive gain was present during false alarms, while a large negative gain was present in misses.


Hit trials had a significantly greater link weight, fewer neurons per subnetwork, and a greater number of subnetworks compared to passive and miss trials. In contrast, incorrect behavioral choices (misses and false alarms) were associated with larger networks but no significant changes in link strength. Thus, correct decisions are associated with compact and stronger networks. In comparison to a pure-tone detection task, pure-tone frequency discrimination involves both target and non-target sounds. The results suggest that decision-making during frequency discrimination evokes different changes for target vs. non-target sounds in both the response amplitude and functional connectivity of neurons in A1.


We trained mice to perform an auditory discrimination task while using 2-photon imaging to study the activity of neuronal populations with single cell resolution in primary auditory cortex (A1). We found that both the amplitude of neural responses to sounds, and the way that neurons interact reflected the behavioral choices made during task performance. Thus, the results indicate that behavioral choice modulates neuronal circuits already in A1, and that task related plasticity in A1 depends on the behavioral meaning of a sound.


To study the neural basis of decision-making in primary auditory cortex (A1), we trained 9 transgenic CBA x Thy1-GCaMP6s F1 mice to perform a pure-tone frequency discrimination task during in vivo 2-photon (2P) Ca2+ imaging experiments in A1 (Fig 1). Head-fixed mice were trained to lick a waterspout in response to a low-frequency target tone (7 or 9.9 kHz, red), and to avoid licking the waterspout after hearing a high-frequency non-target tone (14 or 19.8 kHz, 88 blue). The four frequencies were randomized across trials. The mice were trained to withhold behavioral responses for 0.5 s after the onset of a target tone in order to receive the reward of a water droplet. This waiting period enabled us to assess neural responses before the animal indicated its decision.
Each trial’s behavioral response was categorized as a hit (licking after target onset), miss (no licking after a target), false alarm (licking after non-target onset), or correct rejection (no licking in response to a non-target). Incorrect behavioral responses were punished with an 8 s time-out added to the ITI.

![alt tag](https://user-images.githubusercontent.com/57324666/89338460-9c935480-d66a-11ea-8d41-5da1b4d4a13c.jpg)

Figure 1. Head-fixed pure-tone frequency discrimination task. a. 9 head-fixed mice were trained to discriminate low-frequency target tones (red) vs high-frequency non-target tones (blue). b.  Average lick rates within a trial during task performance. Horizontal black bar shows when the tone was presented. The red trace shows the lick rate for hits (H). The blue trace shows the lick rate for false alarms (F). c. Average performance rates (i.e., H and F rates) for each presented tone frequency. Error bars show two standard errors of the mean (SEMs; n=35 experiments). d.  Cumulative distribution functions (CDFs) for H and F rates.





Whether you write your book's content in Jupyter Notebooks (`.ipynb`) or
in regular markdown files (`.md`), you'll write in the same flavor of markdown
called **MyST Markdown**.

## What is MyST?

MyST stands for "Markedly Structured Text". It
is a slight variation on a flavor of markdown called "CommonMark" markdown,
with small syntax extensions to allow you to write **roles** and **directives**
in the Sphinx ecosystem.

## What are roles and directives?

Roles and directives are two of the most powerful tools in Jupyter Book. They
are kind of like functions, but written in a markup language. They both
serve a similar purpose, but **roles are written in one line**, whereas
**directives span many lines**. They both accept different kinds of inputs,
and what they do with those inputs depends on the specific role or directive
that is being called.

### Using a directive

At its simplest, you can insert a directive into your book's content like so:

````
```{mydirectivename}
My directive content
```
````

This will only work if a directive with name `mydirectivename` already exists
(which it doesn't). There are many pre-defined directives associated with
Jupyter Book. For example, to insert a note box into your content, you can
use the following directive:

````
```{note}
Here is a note
```
````

This results in:

```{note}
Here is a note
```

In your built book.

For more information on writing directives, see the
[MyST documentation](https://myst-parser.readthedocs.io/).


### Using a role

Roles are very similar to directives, but they are less-complex and written
entirely on one line. You can insert a role into your book's content with
this pattern:

```
Some content {rolename}`and here is my role's content!`
```

Again, roles will only work if `rolename` is a valid role's name. For example,
the `doc` role can be used to refer to another page in your book. You can
refer directly to another page by its relative path. For example, the
role syntax `` {doc}`intro` `` will result in: {doc}`intro`.

For more information on writing roles, see the
[MyST documentation](https://myst-parser.readthedocs.io/).


### Adding a citation

You can also cite references that are stored in a `bibtex` file. For example,
the following syntax: `` {cite}`holdgraf_evidence_2014` `` will render like
this: {cite}`holdgraf_evidence_2014`.

Moreoever, you can insert a bibliography into your page with this syntax:
The `{bibliography}` directive must be used for all the `{cite}` roles to
render properly.
For example, if the references for your book are stored in `references.bib`,
then the bibliography is inserted with:

````
```{bibliography} references.bib
```
````

Resulting in a rendered bibliography that looks like:

```{bibliography} references.bib
```


### Executing code in your markdown files

If you'd like to include computational content inside these markdown files,
you can use MyST Markdown to define cells that will be executed when your
book is built. Jupyter Book uses *jupytext* to do this.

First, add Jupytext metadata to the file. For example, to add Jupytext metadata
to this markdown page, run this command:

```
jupyter-book myst init markdown.md
```

Once a markdown file has Jupytext metadata in it, you can add the following
directive to run the code at build time:

````
```{code-cell}
print("Here is some code to execute")
```
````

When your book is built, the contents of any `{code-cell}` blocks will be
executed with your default Jupyter kernel, and their outputs will be displayed
in-line with the rest of your content.

For more information about executing computational content with Jupyter Book,
see [The MyST-NB documentation](https://myst-nb.readthedocs.io/).
