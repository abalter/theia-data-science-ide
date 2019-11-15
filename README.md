# Project Proposal:
# Open-Source, Platform Agnostic, IDE Based on the Theia Framework for (Data) Scientific Computing

## TL/DR
I propose that "the community" use the [Theia](https://theia-ide.org/) framework to build an open-source IDE that combines the best of RStudio, Spyder, and Jupyter (etc.) into a data science IDE that is cloud/desktop agnostic _and_ language agnostic.

## Contents
  - [Introduction](#introduction)
  - [The Good News](#the-good-news)
  - [The Bad News](#the-bad-news)
  - [More about Theia](#more-about-theia)
  - [Why not use Plugins?](#why-not-use-plugins)
  - [Feature Comparison Chart (proposed)](#feature-comparison-chart-proposed)

## Introduction
As far as I can tell, the Data Science / Science community primarily uses three coding environments:

* Jupyter\[lab\] Notebooks
* RStudio
* Spyder

Each has their strengths and weaknesses, pros and cons, adherents and detractors. I personally avoided R and RStudio
for a long time in favor of Python, Spyder, and Jupyter. My most recent position is in an RStudio
shop. I have discovered that RStudio is a migical world that seemlessly
integrates script files, notebooks, exploring variables, maintaining history, accessing files, loading
data, and an interactive command line (both R and bash). Fantastically, the RStudio IDE has both a cloud and desktop version.

Taking in to accout what I have seen in academia, and extending this to my perceptions of industry as well, 
RStudio reigns predominent in terms of daily usage among these disciplines. Rstudio is supported by a large, profitable organization which does a fantastic job with this product. The RStudio company does release open-sourced versions, but stripped
of some important functionality. While technically open source, these versions are not community maintained. Consequently, or by design, the roadmap
and development move forward at the sole command of the RStudio company.

I propose developing a free, open-source, data science IDE that combines the best features of the existing commercial and open source options out there.

[Chart below](#feature-comparison-chart-proposed).

## The Good News
We would not need to build a one-off project from the ground such as with [Spyder](https://www.spyder-ide.org/), [Jupyter Notebook](https://jupyter.org/), [Architect](https://www.getarchitect.io/), or [Rodeo](https://github.com/yhat/rodeo) (which was eventually abandoned; [see discussion](https://github.com/yhat/rodeo/issues/655#issuecomment-507076811)). Quite the opposite. _We would build on an existing framework and get professional support for our **own** development issues._

The Eclipse foundation [hosts and develops](https://projects.eclipse.org/projects/ecd.theia) an IDE Framework called [Theia](https://theia-ide.org/) for building platform agnostic (cloud/desktop) IDEs ([More below](#Theia)). This is modern,
flexible, extensible, and uses the latest build technologies. Importantly, Theia was designed by intention from the ground up to work on the desktop and in the cloud
without needing to create a parallel code base. 

Theia IS being very actively developed.

![Thiea development activity][theia-activity]
_Development activity on github._

Not only can _we_ get support directly from Eclipse, the very act of building our IDE would likely contribute new ideas and code to the Theia project, creating the sort of positive feedback loop that is one of the _shining hallmarks of open-source development_.


## The Bad News
While I am idealistic, passionate, and a very good scientific programmer, I am not a _developer_. I'm also old-ish, have a lot of 
family obligations, and am trying to carve out a career for myself in a new field (namely biomedical data science). I neither have the skill nor
the bandwidth to LEAD this project. However, _I swear upon all that is good and true_ that if some person or group
would come forward to _lead_ the software development, I would take on a **strong** supporting role by responding
to issues, coding bits and pieces (menu here, UI tweak there), writing documentation, testing, fixing small problems, looking for sponsors,
etc. 

## More about Theia
[Wikipedia tells us that](https://en.wikipedia.org/wiki/Eclipse_Theia#History) 

>Theia was developed by TypeFox and Ericsson, with additional contributions from Red Hat, IBM, Google and Arm Holdings. It was first launched in March 2017. Since May 2018, Theia has been a project of the Eclipse Foundation. 

If you search the 'net, many people refer to Theia as an IDE. However Theia developers fom Eclipse try to emphasize that Theia is a _framework to build your own IDE_ just as they did with their own [Che editor]([editor](https://www.eclipse.org/che/)) and [GitPod](https://www.gitpod.io/) (which by the way is awesoms). ([differences between Che and Theia]((which by the way is awesoms))).


Another common misconception is that Theia is a VS Code clone. This stems from the fact that in addition to having some of VS Code's look and feel, Theia  can actually use VS Code plugins. However, Theia is a completely independent code base.

Other real life examples are [Microclimate](https://microclimate.dev/usingmicroclimate), potential [GitLab integration](https://gitlab.com/groups/gitlab-org/-/epics/1619), the new [Arduino Pro IDE](https://blog.arduino.cc/2019/10/18/arduino-pro-ide-alpha-preview-with-advanced-features/), [Hyperexponential's infrasturcture](https://webcache.googleusercontent.com/search?q=cache:KD4zb6vG_e8J:https://www.hyperexponential.com/jobs/typescript-engineer/+&cd=28&hl=en&ct=clnk&gl=us&client=firefox-b-1-d).




[theia-activity]: theia-activity.png "Theia development activity on GitHub."


## Why not use Plugins?
>Why not just use existing technology (Atom, VS Code, Theia, Jupyter) and build it out with plugins?

The plugin model seems like fun&mdash;everyone gets to contribute and users get lots of options. But for serious tools this model fails. Essential functionality (code linting, markdown preview, variable explorer, kernel integration, ...) becomes dependent on individuals in the community implementing versions of these features **AND** dedicating themselves to support them for eternity. Insted, plugins tend to stall out or become totally abandoned as quickly as they are created. 

On the other side of things, the pluginverse become flooded with options making it hard to know which to use. There are currently a multitude markdown previwers for VS Code. Some have more features than others. Some work better than others. Hhow do you pick which to use? You have to try them all first and/or read many reviews; and then hope that development continues and bugs are fixed. If things don't work out, you need to find another plugin.

Consider the data science plugins for Atom and VS Code. There are multiple ones for R with non-overlapping feature sets, and some of the most robust [have already been abandoned](https://github.com/microsoft/RTVS)   .

(In writing this in VS Code, I tried one markdown previewer that improperly added line breaks at each newline character in the source and rendered text inside escaped square brackets \\[...\\] as math. I switched to another that is ok with that, but this one uses a markdown flavor that requires me to use an explicit \&mdash; rather than \-\-\-.)

That is why I believe the project needs to be curated at the top level by a group of people who will take input from the community and make wise decisions. This has largely been how the Jupyter project has gone. However there are a growing number of [unofficial extensions](https://github.com/ipython-contrib/jupyter_contrib_nbextensions). It will remain to be seen how well this works out. 

Theia _does_ have an a plugin interface, can use existing VS code plugins, and is designed to be extended with more deeply rooted _extensions_. Thus, the community is welcome to add new functionality. Plugins that have shown themselves to be popular, useful, and stable could be curated (i.e. incorporated) in to the main code base and be maintained by others even if the original plugin author moves on to other things.


## Feature Comparison Chart (proposed)
I have filled this table in to the best of my knowledge. I do not currenlty use Spyder or Hydrogen, and have not fully explored data science options for VS Code. _**PLEASE** help make this chart more complete and accurate with your suggestions and input!_

|                                                                             | Jupyter                                                   | RStudio | Spyder   | VS Code                              | Hydrogen                                      | Proposal        |
|-----------------------------------------------------------------------------|-----------------------------------------------------------|---------|----------|--------------------------------------|-----------------------------------------------|-----------------|
| IDE-like environment                                                        | No                                                        | Yes     | Yes      | Yes                                  |                                               | Yes             |
| Real-time notebook rendering                                                | Yes                                                       | No      |          | No                                   | Yes                                           | Yes             |
| Visual notebook editing                                                     | Yes                                                       | No      | ??       | Possibly with plugin                 | Yes                                           | Yes             |
| Plain text notebook editing                                                 | No                                                        | Yes     | ??       | Possibly with Plugin                 | Yes                                           | Yes             |
| Multiple notebook formats                                                   | No                                                        | No      | No       | Possibly with plugin                 | No                                            | Yes             |
| Notebook-Focused                                                            | Yes                                                       | No      | No       | No                                   | Yes                                           | Yes             |
| Development-Focused                                                         | No                                                        | Yes     | Yes      | Yes                                  | No                                            | Yes             |
| Data science focused                                                        | Yes                                                       | Yes     | Somewhat | Poor plugin options                  | Yes                                           | Yes             |
| Edit code and notebooks side by side                                        | Somewhat                                                  | Yes     | Yes      | Possibly with plugins                | To the extent that Hydrogen runs in an IDE... | Yes             |
| Notebook linked to command line                                             | Awkward choice of console format.                         | Yes     | ??       | ??                                   | N/A                                           | Yes             |
| Shared environment for notebooks, scripts, and command line                 | Partial--can create individule console for each notebook. | Yes     | Yes      | ??                                   | N/A                                           | Yes             |
| Each notebook needs/gets it's own console.                                  | Yes                                                       | No      | ??       | ??                                   | N/A                                           | Yes, if wanted. |
| Multiple parallel execution environments (kernels)                          | Yes                                                       | No      | ??       | ??                                   | No                                            | Yes             |
| Multi-language support in notebooks                                         | Yes                                                       | Yes     | ??       | ??                                   | Yes                                           | Yes             |
| Multi-language support in IDE                                               | Yes                                                       | No      | No       | ??                                   | N/A                                           | Yes             |
| Variable Explorer                                                           | Primitive                                                 | Yes     | Yes      | No                                   | Yes                                           | Yes             |
| Robust file browser                                                         | No                                                        | Yes     | Yes      | Yes                                  | ??                                            | Yes             |
| Easily import data in to computational environment.                          | No                                                        | Yes     | ??       | ??                                   | ??                                            | Yes             |
| Delegates important functionality to community supported plugins/extensions | Yes                                                       | No      | No       | Yes                                  | ??                                            | No              |
| Curates and includes solid implementations of important features.           | No                                                        | Yes     | Yes      | Not for data science.                | Yes                                           | Yes             |
| Maintains command history for console.                                      | No                                                        | Yes     | Yes      | ??                                   | N/A                                           | Yes             |
| Designed for browser and Desktop                                            | No                                                        | Yes     | No       | No                                   | No                                            | Yes             |
| Works in browser                                                            | Yes                                                       | Yes     | No       | There is a separate browser version. | No                                            | Yes             |
| Works on desktop                                                            | No                                                        | Yes     | Yes      | Yes                                  | Yes                                           | Yes             |
| Integrated Git support                                                      | With extension                                            | Yes     | Yes      | Yes                                  | No                                            | Yes             |
| Integrated Conda Support                                                    | Yes with extension                                        | No      | No       | No                                   | No                                            | Yes             |
| Robust enterprise support                                                   | No                                                        | Yes     | No       | Yes                                  | No                                            | No              |
| Robust community support                                                    | Yes                                                       | Yes     | Somewhat | Yes                                  | Somewhat                                      | Hopefully.      |
| Completely free and open source                                             | Yes                                                       | No      | Yes      | No                                   | Yes                                           | Yes             |




