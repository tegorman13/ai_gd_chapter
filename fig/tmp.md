Provide latex tikz code to create a high-level figure to demonstrate the IPO framework for my paper on AI and human decision making. The figure should be publication quality.

The figure is generated, but there are some rendering issues - causing much of the text to overlap, and the boxes to overlap, or text spill outside of the boxes. Rework the tikz code to resolve these issues - and ensure it is generated so that text within boxes does not spill out, and that no text overlaps. Also make it so that the "Trust in AI" points at both the Processing and output boxes. 

# current code: 



\documentclass[tikz,border=5mm]{standalone}
\usepackage{tikz}
\usetikzlibrary{arrows.meta, positioning, fit, calc}

\begin{document}
\begin{tikzpicture}[
    every node/.style={font=\footnotesize\linespread{0.85}\selectfont},
    box/.style={
        rectangle, 
        rounded corners=5pt,
        draw=black!80,
        thick,
        align=center,
        inner sep=12pt
    },
    inputbox/.style={
        box,
        fill=orange!8,
        text width=6cm,
        minimum height=5cm
    },
    processbox/.style={
        box,
        fill=blue!8,
        text width=6cm,
        minimum height=5cm
    },
    outputbox/.style={
        box,
        fill=green!8,
        text width=6cm,
        minimum height=5cm
    },
    moderatorbox/.style={
        rectangle,
        rounded corners=3pt,
        draw=black!50,
        thick,
        fill=white,
        align=center,
        inner sep=5pt,
        text width=3.8cm,
        minimum height=1.2cm,
        font=\scriptsize\bfseries\color{black!70}
    },
    arrow/.style={
        thick,
        -{Stealth[length=3mm, width=2mm]},
        draw=black!60
    }
]

% Main IPO nodes
\node[inputbox] (input) {
    \textbf{\large Input} \\[8pt]
    Human Members \\ (Expertise, Knowledge, Biases) \\[8pt]
    AI Systems \\ (Data, Algorithms, Recommendations) \\[8pt]
    Task \& Context \\ (Complexity, Environment)
};

\node[processbox, right=2.8cm of input] (process) {
    \textbf{\large Processing} \\[8pt]
    Information Search \& Retrieval \\ (Human \& AI) \\[8pt]
    Communication \& Sharing \\[8pt]
    Interpretation \& Integration \\[8pt]
    Shared Mental Models \\[8pt]
    Consensus Formation
};

\node[outputbox, right=2.8cm of process] (output) {
    \textbf{\large Output} \\[8pt]
    Decision Quality \\ (Accuracy, Speed, Errors) \\[8pt]
    Trust \& Reliance \\[8pt]
    Satisfaction \& Acceptance \\[8pt]
    Group Polarization
};

% Moderator nodes
\node[moderatorbox, above=1.8cm of process] (moderator1) {Task Characteristics};
\node[moderatorbox, below=1.8cm of process] (moderator2) {Contextual Factors};
\node[moderatorbox, above=2cm of output, xshift=-3cm] (moderator3) {Trust in AI};

% Main flow arrows
\draw[arrow, shorten >=2pt, shorten <=2pt] (input) -- (process);
\draw[arrow, shorten >=2pt, shorten <=2pt] (process) -- (output);

% Moderator arrows
\draw[arrow] (moderator1.south) to[out=-90, in=90] (process.north);
\draw[arrow] (moderator2.north) to[out=90, in=-90] (process.south);

% Improved "Trust in AI" arrows
\draw[arrow] ($(moderator3.south west)!0.3!(moderator3.south)$) |- (process.east);
%\draw[arrow] ($(moderator3.south east)!0.3!(moderator3.south)$) |- (output.north);

% Dashed influence arrows
\draw[arrow, dashed] (moderator1.east) -| ([xshift=15mm]output.north west);
\draw[arrow, dashed] (moderator2.east) -| ([xshift=15mm]output.south west);

% Framework bounding box
\node[draw=black!50, dashed, thick, rounded corners=8pt, 
       fit=(input) (process) (output) (moderator1) (moderator2) (moderator3),
       inner xsep=12pt, inner ysep=12pt] (frame) {};

% Title
\node[above=5mm of frame.north, anchor=south, 
       font=\bfseries\large\color{black!80}, fill=white, inner sep=3pt] 
    {Information Processing Framework for Human-AI Group Decision Making};

\end{tikzpicture}
\end{document}





# Terminal Output: 

(base) thomasgorman@TG-Macbook fig % pdflatex f7.tex


This is pdfTeX, Version 3.141592653-2.6-1.40.26 (TeX Live 2024) (preloaded format=pdflatex)
 restricted \write18 enabled.
entering extended mode
(./f7.tex
LaTeX2e <2024-11-01> patch level 1
L3 programming layer <2024-12-25>
(/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/standalone/standalone.cls
Document Class: standalone 2022/10/10 v1.3b Class to compile TeX sub-files standalone
(/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/tools/shellesc.sty) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/iftex/ifluatex.sty (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/iftex/iftex.sty)) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/xkeyval/xkeyval.sty (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/xkeyval/xkeyval.tex (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/xkeyval/xkvutils.tex (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/xkeyval/keyval.tex)))) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/standalone/standalone.cfg) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/base/article.cls
Document Class: article 2024/06/29 v1.4n Standard LaTeX document class
(/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/base/size10.clo))) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/pgf/frontendlayer/tikz.sty (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/pgf/basiclayer/pgf.sty (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/pgf/utilities/pgfrcs.sty (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/utilities/pgfutil-common.tex) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/utilities/pgfutil-latex.def) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/utilities/pgfrcs.code.tex (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/pgf.revision.tex))) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/pgf/basiclayer/pgfcore.sty (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/graphics/graphicx.sty (/Users/thomasgorman/Library/TinyTeX/nyTeX/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzlibraryshapes.geometric.code.tex (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/libraries/shapes/pgflibraryshapes.geometric.code.tex)) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzlibraryarrows.code.tex (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/libraries/pgflibraryarrows.code.tex)) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzlibrarypositioning.code.tex) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzlibraryfit.code.tex) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/generic/pgf/frontendlayer/tikz/libraries/tikzlibrarybackgrounds.code.tex) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/l3backend/l3backend-pdftex.def) (./f7.aux) (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/epstopdf-pkg/epstopdf-base.sty (/Users/thomasgorman/Library/TinyTeX/texmf-dist/tex/latex/latexconfig/epstopdf-sys.cfg))



! Package pgfkeys Error: The key '/tikz/variable' requires a value. I am going to ignore this key.

See the pgfkeys package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.105 \node [variable, above=2.5cm of process]
                                               (moderator1) {Task Characteri...
?

! Package pgfkeys Error: The key '/tikz/variable' requires a value. I am going to ignore this key.

See the pgfkeys package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.106 \node [variable, below=2.5cm of process]
                                               (moderator2) {Contextual Fact...
?

! Package pgfkeys Error: The key '/tikz/variable' requires a value. I am going to ignore this key.

See the pgfkeys package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.107 \node [variable, above=1.5cm of output]
                                              (moderator3) {Trust in AI};
?

! Package pgfkeys Error: The key '/tikz/variable' requires a value. I am going to ignore this key.

See the pgfkeys package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.59 ...above of=output, xshift=1cm, yshift=1.5cm]
                                                   {Trust in AI};
?
Missing character: There is no [ in font nullfont!
Missing character: There is no d in font nullfont!
Missing character: There is no a in font nullfont!
Missing character: There is no s in font nullfont!
Missing character: There is no h in font nullfont!
Missing character: There is no e in font nullfont!


! Package pgfkeys Error: I do not know the key '/tikz/padding', to which you passed '0.5cm', and I am going to ignore it. Perhaps you misspelled it.

See the pgfkeys package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.69 ...ding=0.5cm, draw, dashed, inner sep=0.2cm]
                                                   (frame) {};
?

[1{/Users/thomasgorman/Library/TinyTeX/texmf-var/fonts/map/pdftex/updmap/pdftex.map}] (./f7.aux) )</Users/thomasgorman/Library/TinyTeX/texmf-dist/fonts/type1/public/amsfonts/cm/cmbx10.pfb></Users/thomasgorman/Library/TinyTeX/texmf-dist/fonts/type1/public/amsfonts/cm/cmr10.pfb></Users/thomasgorman/Library/TinyTeX/texmf-dist/fonts/type1/public/amsfonts/cm/cmr8.pfb>
Output written on f7.pdf (1 page, 47303 bytes).
Transcript written on f7.log.



# Paper Outline and working plan: 


1. **Strengthen the IPO Framework:** Instead of simply stating the IPO framework, explicitly demonstrate how each section (Inputs, Processing, Outputs) represents a distinct stage in group decision-making *with AI*.
    *   *Inputs*: Emphasize that this section is about the resources, information, and knowledge available to the group, and how AI alters access, and availability.
    *   *Processing*: This is where the group interacts, deliberates, shares information and develops a shared understanding, and where AI's role as a facilitator, mediator, or active participant becomes crucial.
    *   *Outputs*: Focus on the actual decisions made, and how they differ in quality, speed, and acceptance when AI is involved.
2. **Integrate Moderating Variables:** You mentioned trust as a potential moderating variable. Other variables like task complexity, group diversity, AI transparency (explainability), and user interface design could also significantly impact the IPO process in AI-assisted group decision-making. Weave these variables into the relevant IPO sections rather than treating them as an afterthought.
3. **Elaborate on Group Polarization:** This is a crucial concept, especially given AI's potential to create filter bubbles and echo chambers. Dedicate a specific subsection to it, either within "Processing" or as a separate section after the IPO framework, where you discuss the implications for AI-assisted groups.
4. **Theorize More Explicitly:** You mention bounded rationality and the fit of strategies to the environment. These are excellent theoretical anchors. Use them more explicitly to frame your arguments and interpret the findings of the empirical studies you cite. For example, you could discuss how AI might mitigate or exacerbate the effects of bounded rationality in group settings.
5. **Emphasize the "So What?":** For each section, especially the future directions, clearly articulate the implications of the research you're discussing. What do these findings mean for the design of AI systems, for group dynamics, and for decision-making processes in organizations and society?
6. **Add a Section on Challenges and Limitations:** Before the conclusion, add a section that explicitly addresses the challenges and limitations of using AI in group decision-making. This will add balance and nuance to your chapter, further, addressing ethical considerations, such as algorithmic bias, fairness, accountability, and transparency, will demonstrate a comprehensive understanding of the topic. This section could also cover the potential negative impacts on human skills and critical thinking.

## Detailed Outline of the Chapter

Here is a detailed outline based on the above suggestions, incorporating relevant citations from your materials:

**AI and Group Decision Making: An Information Processing Perspective**

**I. Introduction**

*   Briefly introduce the increasing role of AI in group decision-making.
*   Highlight the opportunities (enhanced efficiency, accuracy, innovation) and challenges (trust, biases, transparency, ethics) of human-AI collaboration.
*   Introduce the information processing framework (Inputs-Processing-Outputs) as a lens for analysis (Hinsz et al., 1997).
*   State the key questions the chapter will address within the IPO framework.
*   Provide a roadmap of the chapter's structure.

**II. Inputs: Resources and Information in AI-Assisted Groups**

*   *A. Defining the Input Stage:*

    *   Explain that this section focuses on the resources available to groups, including information, knowledge, and expertise.
    *   Discuss how AI alters the landscape of available resources.
*   *B. Group Member Roles and Expertise:*

    *   Discuss the importance of role assignment in traditional groups.
    *   Introduce the complexities of role assignment in human-AI teams.
    *   Explore how humans allocate tasks between themselves and AI agents (Marjieh et al., 2024).
    *   Discuss the need to move beyond human-human team paradigms in human-autonomy teams (HATs) (McNeese et al., 2023).
    *   Highlight the potential of AI agents to take on diverse roles (devil's advocate, mediator, etc.) (Chiang et al., 2024).
    *   Discuss how AI can help identify missing expertise or knowledge within a group (Narayanan & Feigh, 2024).
    *   Explore the concept of diversity in human-AI teams, considering both human and AI characteristics (Cui & Yasseri, 2024).
    *   *Future Directions:* Research on optimal role allocation strategies in HATs, AI's ability to dynamically adapt its role based on group needs, developing metrics for "team diversity" that include AI agents.
*   *C. Information Search and Retrieval:*

    *   Describe how AI, particularly LLMs, enhances data retrieval capabilities (Bouschery et al., 2023; Burton et al., 2024; Si et al., 2024; Wang et al., 2024).
    *   Discuss how AI can synthesize information from diverse sources, potentially improving the quality of information available to groups (Burton et al., 2024; Flores et al., 2024; Zheng et al., 2024).
    *   Address the risks associated with AI-assisted information search, such as filter bubbles, echo chambers, and overreliance (Anderl et al., 2024; Sharma et al., 2024; Stadler et al., 2024).
    *   Highlight the importance of retrieval-augmented generation (RAG) in improving LLM outputs (Si et al., 2024; Wang et al., 2024).
    *   Discuss the role of user interface design in mitigating risks and promoting effective information search (Buçinca et al., 2021).
    *   Discuss how AI can be used to analyze and understand the structure of the information environment (Bhatia, 2023).
    *   *Future Directions:* Research on how to design AI systems that promote diverse information exposure, how to balance AI assistance with human critical evaluation, how to optimize human-AI collaboration in complex search tasks.
*   *D. Knowledge Sharing and Communication:*

    *   Introduce the concept of transactive memory systems (TMS) and their importance in group decision-making (Wegner, 1987; Yan et al., 2021).
    *   Present empirical findings on how AI can serve as a unique knowledge repository within human-AI teams (Bienefeld et al., 2023).
    *   Discuss the potential of AI to overcome social barriers to information sharing.
    *   Discuss the potential of AI to facilitate communication and coordination within teams (Bastola et al., 2024; Ma et al., 2024; Sidji et al., 2024; Yang et al., 2024).
    *   Address the challenges of designing AI systems that effectively communicate with humans, considering factors such as timing, modality, and transparency (Radivojevic et al., 2024; S. Zhang et al., 2024; Zhou & Gorman, 2024).
    *   Consider the impact of AI communication on trust and team cohesion (Chuang et al., 2024; Nishida et al., 2024; Zvelebilova et al., 2024).
    *   *Future Directions:* Research on how to design AI systems that promote effective TMS development in human-AI teams, how to optimize AI communication strategies for different team compositions and tasks, how to measure and improve shared understanding in human-AI teams.

**III. Processing: Group Deliberation and Integration with AI**

*   *A. Defining the Processing Stage:*

    *   Explain that this section focuses on how groups deliberate, integrate information, and form consensus.
    *   Highlight the unique challenges and opportunities AI introduces to group processing.
*   *B. Cognitive Load and Cognitive Forcing Functions:*

    *   Discuss how AI assistance can influence cognitive load during decision-making.
    *   Present findings on the effectiveness of cognitive forcing functions in reducing overreliance on AI (Buçinca et al., 2021).
    *   Address the trade-off between reducing overreliance and increasing cognitive load/decreasing user satisfaction.
    *   Discuss the moderating role of individual differences, such as Need for Cognition (Buçinca et al., 2021).
    *   Introduce other potential moderating variables, such as task complexity and user interface design.
    *   *Future Directions:* Research on how to personalize cognitive forcing functions based on individual needs and preferences, how to design interfaces that balance cognitive engagement with ease of use, how to measure and optimize cognitive load in human-AI teams.
*   *C. Consensus Formation and AI Mediation:*

    *   Discuss the challenges of achieving consensus in diverse groups.
    *   Present findings on the potential of AI to mediate group discussions and facilitate consensus formation (Tessler et al., 2024).
    *   Highlight the ability of AI to incorporate minority opinions and prevent majority dominance.
    *   Discuss the implications of AI-mediated consensus for democratic deliberation and collective decision-making.
    *   *Future Directions:* Research on how to design AI systems that are sensitive to group dynamics and power imbalances, how to ensure fairness and transparency in AI-mediated consensus, how to evaluate the long-term impact of AI mediation on group cohesion and decision quality.
*   *D. Group Polarization and Echo Chambers:*

    *   Define group polarization and explain its relevance to AI-assisted decision-making.
    *   Discuss the potential for AI to exacerbate group polarization by reinforcing existing biases and limiting exposure to diverse perspectives.
    *   Address the risks of filter bubbles and echo chambers in AI-mediated communication (Sharma et al., 2024).
    *   Explore potential solutions, such as incorporating "devil's advocate" AIs (Chiang et al., 2024) or using AI to promote exposure to diverse viewpoints.
    *   *Future Directions:* Research on how to detect and mitigate group polarization in AI-assisted settings, how to design AI systems that promote constructive disagreement and critical evaluation of diverse perspectives, how to measure the long-term impact of AI on group diversity and polarization.
*   *E. Shared Mental Models:*

    *   Emphasize the role of shared mental models in effective teamwork (N. J. McNeese et al., 2023; Narayanan & Feigh, 2024).
    *   Discuss the challenge of developing shared mental models in human-AI teams due to the opacity of AI reasoning (Collins et al., 2024; S. Zhang et al., 2024).
    *   Explore potential solutions, such as increasing AI transparency, providing explanations, or using interactive interfaces (Chiang et al., 2024; Klieger et al., 2024; Ma et al., 2024; Sidji et al., 2024).
    *   *Future Directions:* Research on how to measure and visualize shared mental models in human-AI teams, how to design AI systems that actively contribute to the development of shared understanding, how to adapt AI behavior based on the evolving mental models of human teammates.

**IV. Outputs: Decision Quality, Reliance, and Team Dynamics**

*   *A. Defining the Output Stage:*

    *   Explain that this section focuses on the outcomes of AI-assisted group decision-making, including decision accuracy, speed, user satisfaction, and team dynamics.
*   *B. Decision Accuracy and Complementarity:*

    *   Define complementarity and discuss the conditions under which human-AI teams can outperform either humans or AI alone (Rastogi et al., 2023; Steyvers et al., 2022).
    *   Present empirical findings on the factors that influence complementarity, such as task structure, information asymmetry, and AI capabilities (Becker et al., 2022; S. Liu & Steyvers, 2024; Shin et al., 2023).
    *   Discuss the importance of aligning human and AI strengths (A. Kumar et al., 2024; Lu et al., 2024).
    *   *Future Directions:* Research on how to design AI systems that are specifically tailored to complement human decision-making strengths, how to dynamically allocate tasks between humans and AI based on real-time performance, how to measure and predict complementarity in different domains.
*   *C. Trust, Reliance, and Utilization:*

    *   Discuss the central role of trust in human-AI collaboration (Cui & Yasseri, 2024).
    *   Explore the factors that influence trust in AI, such as perceived competence, transparency, and anthropomorphism (Zvelebilova et al., 2024).
    *   Present findings on how trust and confidence affect reliance on AI (Liang et al., 2022; Pescetelli & Yeung, 2021; Steyvers et al., 2024).
    *   Discuss the risks of overreliance and underreliance on AI (Buçinca et al., 2021; Duarte & Campos, n.d.).
    *   Explore strategies for promoting appropriate reliance on AI, such as providing uncertainty estimates or incorporating user feedback (Carlebach & Yeung, 2023; Steyvers et al., 2024).
    *   Discuss the relationship between trust and utilization patterns (Buçinca et al., 2021).
    *   *Future Directions:* Research on how to dynamically calibrate trust in AI based on performance and context, how to design AI systems that are perceived as trustworthy by diverse users, how to measure and mitigate the negative consequences of overreliance and underreliance.
*   *D. Responsibility and Accountability:*

    *   Discuss the challenges of attributing responsibility in human-AI teams (Tsirtsis et al., 2024).
    *   Present findings on how humans perceive the responsibility of AI agents (Narayanan et al., 2023).
    *   Explore the implications for accountability and ethical decision-making.
    *   *Future Directions:* Research on how to design AI systems that support clear and fair attribution of responsibility, how to establish norms and guidelines for accountability in human-AI collaboration, how to address legal and ethical issues related to AI-assisted decision-making.
*   *E. Risk and Bias:*

    *   Discuss how AI can both mitigate and exacerbate human biases in decision-making (Bhatia, 2024; Zhu et al., 2024).
    *   Present findings on the presence of biases in AI systems and their impact on group decisions.
    *   Explore strategies for mitigating bias, such as diverse training data, algorithmic auditing, and human oversight.
    *   *Future Directions:* Research on how to detect and measure bias in AI-assisted group decision-making, how to design AI systems that are robust to biases in human input, how to promote fairness and equity in human-AI collaboration.

**V. Challenges and Limitations**

*   *A. Ethical Considerations:*

    *   Discuss the ethical implications of using AI in group decision-making, including issues of fairness, transparency, accountability, and privacy.
    *   Address the potential for algorithmic bias and discrimination (Barredo Arrieta et al., 2020).
    *   Explore the need for ethical guidelines and regulations for the development and deployment of AI decision aids.
*   *B. Technical Challenges:*

    *   Discuss the limitations of current AI technology, such as the difficulty of achieving true complementarity, the opacity of complex algorithms, and the challenge of creating AI that can understand and adapt to dynamic social contexts.
    *   Address the need for more robust and interpretable AI models.
*   *C. Human Factors Challenges:*

    *   Discuss the potential negative impacts of AI on human skills, critical thinking, and agency (Gerlich, 2025; H. Kumar et al., 2024).
    *   Address the risks of overreliance, automation bias, and deskilling.
    *   Explore strategies for maintaining human engagement and expertise in AI-assisted settings.

**VI. Conclusion**

*   Summarize the key findings and insights from each section of the chapter.
*   Reiterate the importance of the information processing framework for understanding AI-assisted group decision-making.
*   Emphasize the need for interdisciplinary research to address the complex challenges and opportunities in this rapidly evolving field.
*   Offer a final thought on the future of human-AI collaboration and its potential to transform decision-making in organizations and society.
