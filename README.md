<h1 align="center"> Latex-Notes-Showcase </h1>

<img src="assets/coverpage.png">

## General Information.

I won't be removing the information (my notes), as some might find the code for the diagrams and etc useful. There might be some minute mistakes here and there.

### Structure. 
```
Singularity/
├── images/
│   ├── image.png
│   ├── imageb.png
├── equations.tex
└── preamble.sty
```

### Modified Margins.

I have modified the margins in both, to accomodate for the double columns. 

```tex
\topmargin=0in        % distance from top of page to header/text
\evensidemargin=0in   % left margin for even-numbered pages
\oddsidemargin=0in    % left margin for odd-numbered pages
\textwidth=6.5in      % width of the text block
\textheight=9.0in     % height of the text block
\headsep=0.25in       % space between header and main text
```

# Singularity. 

<p align="middle">
  <img src="assets/equations_pages-to-jpg-0001.jpg" width="300" />
  <img src="assets/equations_pages-to-jpg-0003.jpg" width="300" /> 
</p>


## The boxes.

The boxes are made using the `tcolorbox` package. The heading text can be customized (instead of "Question." it can be "Answer.", etc)

### The blue box. (for question)

```tex
\newtcolorbox{question}[1]{   % [1] means it takes 1 argument
    enhanced, 
    colback=yorhabg,
    colframe=mblue,
    coltext=yorhafg,
    coltitle=yorhabg,
    attach boxed title to top left={yshift*=-\tcboxedtitleheight}, 
    title=\texttt{#1},        % use the argument as the title
    boxed title size=title,
    boxed title style={%
        rounded corners=northeast, 
        rounded corners=northwest, 
        colback=tcbcolframe, 
        boxrule=0pt,
    },
    underlay boxed title={%
        \path[fill=tcbcolframe] (title.south west)--(title.south east) 
            to[out=0, in=180] ([xshift=5mm]title.east)--
            (title.center-|frame.east)
            [rounded corners=5pt] |- 
            (frame.north) -| cycle; 
    },
}
```

#### Usage.

```tex
\begin{question}{Question.}   % same as before
This is a sample question.
\end{question}

\begin{question}{Note.}       % now a different title works too
This is just a note instead of a question.
\end{question}
```

*I have hardcoded the heading as "Question." to reduce repitition, so it might different in my notes.*

---
### The red box. 


Without Heading. (doesn't require any parameters at the beginning of an environment)

```tex
\newtcolorbox{imp}{
    enhanced,               % enable advanced features
    arc=0mm,                % no rounded corners
    colback=yorhabg,        % background color
    colframe=mred,          % frame color
    leftrule=10mm,          % thick left border
    coltext=yorhafg,        % text color
    overlay={               % add custom content on top of the box
        \node[
            anchor=west,    % align image to the left edge
            outer sep=2pt   % small spacing from the frame
        ] at (frame.west) {
            \includegraphics[width=6mm]{images/imageb.png} % icon
        };
    }
}
```

With Heading. 
```tex
\newtcolorbox{shortcut}[1]{   % [1] = takes 1 argument for the title
    enhanced,               % enable advanced features
    arc=0mm,                % no rounded corners
    colback=yorhabg,        % background color
    colframe=mred,          % frame color
    leftrule=10mm,          % thick left border
    coltext=yorhafg,        % text color
    coltitle=yorhabg,       % title background color
    title=\texttt{#1},      % dynamic title (passed as argument)
    overlay={               % add icon on top of the box
        \node[
            anchor=west,    % stick to the left edge
            outer sep=2pt   % spacing from border
        ] at (frame.west) {
            \includegraphics[width=6mm]{images/imageb.png} % icon
        };
    }
}
```

The usage pattern is similar to the blue box. 


# YoRHa
