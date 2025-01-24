
1. what kind of ORM are we pursuing in our project? does it including reading manuscripts and converting to digital format or is it just music sheets/scores converting to MIDI/audio file or machine-readable code?

The definitions of OMR and some OMR research includes handwritten manuscripts (https://link.springer.com/chapter/10.1007/978-3-031-41498-5_7?fromPaywallRec=false)

Our project scope right now should not include handwritten manuscripts but offline typeset/printable music sheets/scores

2. Statistical modeling approach may be worth exploring but not sure what that entails
 > [!PDF|red] [[understandingOMR.pdf#page=25&selection=6,1,23,44&color=red|understandingOMR, p.25]]
> > Statistical modeling: most machine learning algorithms are based on statistical models that are able to provide a probability distribution over the set of possible recognition hypotheses. When it comes to recognizing, we are typically interested in the best hypothesis—the one that is proposed as an answer—forgetting the probability given to such hypothesis by the model. However, it could be interesting to be able to exploit this uncertainty. For example, in the standard decomposition of stages in OMR systems, the semantic reconstruction stage could benefit from having a set of hypotheses about the objects detected in the previous stage, instead of single proposals. Then, the semantic reconstruction algorithm could establish relationships that are more logical a priori, although the objects involved have a lower probability according to the object detector. These types of approaches have not been deeply explored in the OMR field. Statistical modeling could also be useful so that the system provides a measure of its confidence about the output. Then, the end user might have a certain notion about the accuracy that has been obtained for the given input. This would be especially useful in an interactive system (see below).

