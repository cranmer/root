MDFILES=Preface.md Introduction.md GettingStarted.md Histograms.md \
	Graphs.md FittingHistograms.md ALittleC++.md CINT.md \
	ObjectOwnership.md Graphics.md FoldersTasks.md InputOutput.md \
	Trees.md MathLibraries.md LinearAlgebra.md AddingaClass.md \
	CollectionClasses.md PhysicsVectors.md Geometry.md PythonRuby.md \
	TutorialsandTests.md ExampleAnalysis.md Networking.md Threads.md \
	PROOF.md WritingGUI.md ROOTandQt.md HTMLDoc.md InstallandBuild.md
	
OPTIONS=-s -S -f markdown --toc --chapters --number-sections
OPTIONSHTML=-H css/github.css --mathjax
OPTIONSEPUB=--mathml
OPTIONSPDF=--variable=geometry:a4paper -V geometry:margin=1.5cm

.PHONY: pdf html tex epub

all: pdf html tex epub

pdf: $(MDFILES)
	pandoc $(OPTIONS) $(OPTIONSPDF) $(MDFILES) -o ROOTUsersGuide.pdf

html: $(MDFILES)
	pandoc $(OPTIONS) $(OPTIONSHTML) -t html $(MDFILES) -o ROOTUsersGuide.html

tex: $(MDFILES)
	pandoc $(OPTIONS) -t latex $(MDFILES) -o ROOTUsersGuide.tex

epub: $(MDFILES) metadata.xml title.txt
	pandoc $(OPTIONS) $(OPTIONSEPUB) --epub-metadata=metadata.xml \
	   title.txt $(MDFILES) -o ROOTUsersGuide.epub

clean:
	rm -f ROOTUsersGuide.pdf ROOTUsersGuide.html ROOTUsersGuide.tex ROOTUsersGuide.epub