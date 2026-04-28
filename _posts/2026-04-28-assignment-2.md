---
title: "Assignment 2"
date: 2026-02-26
categories: assignments
---


<h1 style="text-align: center; font-weight: bold;"> Computational Analysis of Science FIction Authors: Stylo and TF-IDF </h1>


## By: Amna Al Mheiri and Mariam Al Junaibi




## Introduction

When we read science fiction novels, such as the ones by H.G. Wells or Leigh Brackett, we get immersed into the setting and atmosphere of the story, the personalities of the characters, and the sense of adventure. On the other hand, a computer does not see the “adventure,” but instead sees the statistical distribution of words like “the,” “and,” and “but.”

To delve deeper into this idea, we will use these two computational methods: Stylo and TF-IDF. The goal is to see whether distant reading can truly capture the essence of science fiction authors from the Project Gutenberg corpus, and to investigate the risks of the use of these computational techniques oversimplifying the complexity of literature from different points in history. In addition, we aim to compare our findings from both methods of computational analysis (Stylometry and TF-IDF) and see if there are any similarities, differences, and consistent patterns between the two.

The corpus we are using consists of eighteen texts from six different science fiction authors. Among these are Leigh Brackett, Andre Alice Norton, and Marion Zimmer Bradley, who were prominent female writers in a field that was largely male-dominated at the time. In fact, Andre Norton even used a masculine pen name to ensure her work was taken seriously by publishers and readers. Even this information we gained from a bit of background research adds context to our analysis that a computer might not pick up on.

We also included Philip K. Dick and Henry Kuttner, who published most of their works in the mid 1900s. This era was heavily impacted by the aftermath of the World Wars, the rise of nuclear technology, and intense Cold War paranoia, all of which has greatly influenced the themes of Dick’s stories. In contrast to these themes of war in Dick’s stories, Kuttner’s work often blurred the line between science fiction and cosmic horror. Kuttner is a particularly interesting case for computational analysis because he frequently collaborated with other writers, such as his wife, C.L. Moore, and Robert Bloch. Henry Kuttner’s book, *The Black Kiss*, was co-authored with Bloch; Kuttner’s *The Ego Machine* was also written in collaboration with C.L. Moore, all in which raises the question of whether Stylo will be able to identify these texts as if only one person wrote them (which are included in our corpus), or if the collaborative writing in these books will cause it to cluster away from Kuttner’s other works.

Finally, we have H.G. Wells, whose works date back to the late 1890s, making him the oldest author in the corpus. For that reason, his texts in the corpus are particularly interesting, especially since one of his nonfiction books, *The Salvaging of Civilization*, is included within the corpus. After some background research, we found that Wells published this book in 1921, shortly after the first World War, and the book is primarily about how humans should work towards a better future and establish better education, cooperation, and leadership to prevent the start of new wars. which he had written after the to see if the computational analysis tools can distinguish this nonfiction text from the other fiction texts.


## Posit Cloud Stylo Analysis

The computational analysis method of Stylometry uses statistical techniques to determine who wrote a text by examining its linguistic traits; this involves looking at word frequency patterns, word arrangement, and other stylistic aspects. Unlike us humans, a computer looks at the “wordlist,” which is the distribution of common function words like “the” and “of,” and after analyzing these patterns, the R Markdown Notebook creates a visual representation of how similar these authors’ writing habits are, regardless of what their stories are about. In our analysis, we used the Stylometry with Science Fiction Authors from PG R Markdown Notebook on Posit Cloud and focused on visualizations showing 500 Most Frequent Words (MFW) in a Cluster Analysis, and 100-2000 MFW in a Bootstrap Consensus Tree Analysis.


<div style="text-align: center;">
 <img src="{{ '/assets/images/CA_500MFW.png' | relative_url }}" style="width: 70%;">
</div>


*Figure 1: 500 MFW Stylometry Cluster Analysis of Science Fiction Corpus.*


In this cluster analysis, we can very clearly see the consistent authorship in some writers. For instance, Norton’s works stay clustered together, which tells us that her unique style of writing remains stable across different stories. The same goes for Philip K. Dick, the computer was able to identify the same style of writing, suggesting that his use of words like “the” or “was” is so consistent that the computer did not get confused.


Several outliers also appear in the cluster. Wells’s *The Salvaging of Civilization* is an outlier because it is a nonfiction book, and Kuttner’s *The Ego Machine* was a book he co-authored with his wife, C.L. Moore, where the computer likely identified the differences in writing style compared to his other books. The most interesting is Zimmer Bradley’s *Jackie Sees A Star*, because despite being science fiction, it clusters away from her other novels. After doing some research, we found that the story revolves around a child (Jackie), meaning it likely has simpler vocabulary which separates it from her other works. This proves that a major change in tone or protagonist in a story can trick the computer’s reading of an author’s style in writing.


<img src="{{ '/assets/images/BCT_100-2000MFW.png' | relative_url }}">


*Figure 2: 100-2000 MFW Stylometry Bootstrap Consensus Tree Analysis of Science Fiction Corpus.*


In this Bootstrap Consensus Tree analysis, we wanted to see if the patterns remain stable across a wonder range of 100 to 2000 words, where the computer looks at more specific words. The results from Dick and Norton remained identical to the first analysis, which shows that their authorial “fingerprints” are incredibly strong even when we count more words.


However, looking at this wider range also confirmed the odd groupings of some texts. Kuttner’s *The Ego Machine* consistently grouped with Zimmer Bradley;s novels rather than his own. Likely because of the specific type of vocabulary of books that primarily take place in space and fall into the subgenre of science fiction called “space opera.” While this Stylo analysis categorizes books based on “style,” it does not examine the topics or the actual content of texts, which is what we will be doing in the next stage of our analysis, where we use TF-IDF to do exactly that.


## TF-IDF Analysis

Unlike Stylo, which highlights the most frequent words, TF-IDF shifts to the more distinguishable terminology, which gives an opportunity to gather information about the specific content-driven signals that differentiate one text from another. We will be examining the corpus pool across three different MFW thresholds (100, 500, and 3000). This allows the visualizations to be explored at different levels of granularity within the same corpus, depending on how much vocabulary is included in the model. The choice of three thresholds, rather than more, is to allow for an in-depth comparative analysis, rather than brief observations.


<img src="{{ '/assets/images/A2100.png' | relative_url }}">


*Figure 3: 100 MFW TF-IDF Analysis of Science Fiction Corpus.*


*Figure 3* presents the results for an analysis at 100 MFW. A striking difference is between Norton and Wells. Norton’s plots are clustered in the lower-right quadrant, suggesting a highly consistent lexical and thematic fingerprint. Conversely, Wells exhibits significant internal variance; while his fiction occupies the right-center, *The Salvaging of Civilization* pulls toward the upper-right extreme, likely reflecting the thematic shift from narrative to sociopolitical discourse. The central convergence of Dick, Kuttner, and Brackett suggests a shared "pulp" vocabulary, whereas Zimmer Bradley’s *Jackie Sees A Star* acts as a distinct outlier, indicating a linguistic profile that diverges sharply from the rest of the corpus.


<img src="{{ '/assets/images/A2500.png' | relative_url }}">


*Figure 4: 500 MFW TF-IDF Analysis of Science Fiction Corpus.*


*Figure 4* presents the results for an analysis at 500 MFW. This demonstrated that increasing the threshold to 500 MFW provides a more granular interrogation of authorial style. While the 100 MFW showed a “pulp” convergence, the 500 MFW plot begins to decompress the central cluster, as the specific thematic vocabularies of Dick and Brackett pull their works into more distinct spatial territories. Notably, the relative positions of Norton, Wells, and the Zimmer Bradley outlier, *Jackie Sees A Star*, remain remarkably stable. Whether the computer looks at 100 or 500 words, their distinctiveness remains unchanged, differentiating them from the rest of the corpus.


<img src="{{ '/assets/images/A23000.png' | relative_url }}">


*Figure 5: 3000 MFW TF-IDF Analysis of Science Fiction Corpus.*


*Figure 5* presents the results for an analysis at 3000 MFW. In comparison to the lower MFWs, the inclusion of lower-frequency vocabulary provides the most distinct separation of authorial and thematic signals. The most significant shift occurs within Kuttner’s corpus; his collaborative work, *The Ego Machine*, pulls sharply away from his other texts, suggesting that at this high threshold, the unique lexicon of his co-author (C.L. Moore) blurs his own stylistic signature. While the "pulp" convergence seen at 100 MFW has completely evaporated into individualized clusters for Dick and Brackett, Norton’s works remain stubbornly grouped. This final stage of analysis highlights the limits of distant reading: while it successfully isolates Wells’s non-fiction and Norton’s consistency, it also begins to "see" the different voices in collaborative works that were invisible at lower word counts.


## Comparing the Stylo and TF-IDF Analyses

The results largely confirm that Stylo specializes in detecting authorship, while TF-IDF is more sensitive to content and genre shifts. In the Stylo analysis, the computer focused on subconscious function words to group the texts by authors, regardless of the plot. However, TF-IDF effectively isolated Wells’s non-fiction, *The Salvaging of Civilization*, pushing it to the extreme margins of the PCA map. This shift occurs because, as Rockwell and Sinclair explain, computers are "cryptographic machines that manipulate codes" rather than meaning; they function as "general-purpose symbol processors" that categorize texts based on formal logical operations (26). Consequently, while Stylo identifies the writer's hand through stable linguistic habits, TF-IDF captures the thematic vocabulary that distinguishes a political manifesto from a science fiction romance by treating their different lexicons as mathematically distinct strings of data.

Co-authorship significantly disrupted the stylistic signatures, particularly for Kuttner. In the Stylo cluster analysis, (*Figure 1*), his collaborative works, such as *The Ego Machine* which is co-authored by C.L. Moore, appeared as outliers in not clustering with his solo novels. This indicates that a second author’s unconscious habits can smudge a primary author’s literary fingerprint. In TF-IDF, this divergence became most visible at 3000 MFW, showing that while collaborators may share a common vocabulary, their unique word choices eventually pull apart at higher levels of granularity.

The shape of the data revealed different insights: Stylo’s hierarchical tree forced texts into rigid branches, emphasizing definitive ancestral links between stories. Conversely, the TF-IDF PCA visualizations used spatial proximity to show a spectrum of style. This allowed us to see the central pulp convergence of Dick, Kuttner, and Brackett in *Figure 3*, a nuance that the Stylo tree obscured. This shift in perspective illustrates Ted Underwood’s argument that statistical models are more than just software; they offer "new methods of representing and interpreting the world" (Underwood 145). By changing the MFW threshold, we aren't just looking at more words; rather we are shifting our method of interpretation from shared genre tropes to idiosyncratic vocabularies.

While the Stylo tree shows who likely wrote a text, the PCA proximity shows how authors from the same era influenced each other's linguistic territory. This transition between models highlights what Underwood describes as the connection between different "scales of description" (Underwood 147). For instance, the tight clustering of Norton across all thresholds proves that her fingerprint is visible at both a small scale (function words) and a large scale (thematic vocabulary). In contrast, the way Kuttner’s collaborative works smudge and pull away at higher MFW counts shows that a new way of representing the data can reveal hidden influences, like a co-author's voice, that a simpler model might overlook.


## Conclusion

Ultimately, this project demonstrates that computational tools, like Stylo and TF-IDF, have nuanced purposes in analyzing writing. By using Stylo to represent the unconscious habits of authors and TF-IDF to represent their conscious thematic choices, we gain a multi-dimensional view of the science fiction corpus. This approach avoids the oversimplification mentioned in the introduction, suggesting that while a computer may not feel the adventure of a Leigh Brackett novel, it can help us interpret the structural and lexical reality that makes that adventure possible.


## Works Cited

Hart, Michael. “Project Gutenberg.” Project Gutenberg, July 1971, www.gutenberg.org/.


Rockwell, Geoffrey, and Stéfan Sinclair. *“The Measured Words: How Computers Analyze Text.”* Hermeneutica: Computer-Assisted Interpretation in the Humanities, MIT Press, 2016, pp. 25-43.


Underwood, Ted. *“The Risks of Distant Reading.”* Distant Horizons: Digital Evidence and Literary Change, U of Chicago P, 2019, pp. 144-74.

**READY FOR GRADING!**