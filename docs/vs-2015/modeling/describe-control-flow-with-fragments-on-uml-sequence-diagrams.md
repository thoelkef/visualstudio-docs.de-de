---
title: Beschreiben des Kontrollflusses mit Fragmenten in UML-Sequenzdiagrammen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: e162b1fdc8f775fc7b4d95249ceeac8d86cd0b74
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836865"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Beschreiben des Kontrollflusses mit Fragmenten in UML-Sequenzdiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einem UML-Sequenzdiagramm können Sie mithilfe von *kombinierten Fragmenten* Schleifen, Verzweigungen und andere Alternativen anzeigen.  
  
 Ein kombiniertes Fragment besteht aus einem oder mehreren *Interaktionsoperanden*, in die jeweils eine oder mehrere Meldungen, Interaktionsverwendungen oder kombinierte Fragmente eingeschlossen sind.  
  
> [!NOTE]
>  In diesem Thema geht es um Fragmente in Sequenzdiagrammen. Weitere Informationen über das Lesen von UML-Sequenzdiagrammen finden Sie unter [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md). Weitere Informationen zum Zeichnen von UML-Sequenzdiagrammen finden Sie unter [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 ![Kombinierte Fragment mit zwei Interaktionsoperanden](../modeling/media/uml-seqfragments.png "UML_SeqFragments")  
  
 In der Abbildung sind die folgenden Elemente dargestellt.  
  
1.  Ein kombiniertes Fragment. Es gibt mehrere Arten von kombinierten Fragmenten. Dieses Beispiel ist ein kombiniertes Alt-Fragment, mit dem Sie anzeigen können, dass alternative Sequenzen von Meldungen auftreten können.  
  
2.  Interaktionsoperanden. Jedes kombinierte Fragment enthält mindestens einen Interaktionsoperanden, der Meldungen, Interaktionsverwendungen und kleinere kombinierte Fragmente enthalten kann. In diesem Beispiel verfügt das kombinierte Alt-Fragment über zwei Interaktionsoperanden, die zwei alternative Sequenzen von Meldungen anzeigen.  
  
3.  Sie können jeden Interaktionsoperanden einzeln auswählen, indem Sie darauf klicken. In diesem Beispiel ist der oberste Interaktionsoperand ausgewählt, sodass seine Begrenzung zu sehen ist. Normalerweise ist nur die Trennlinie zwischen Interaktionsoperanden sichtbar.  
  
    > [!NOTE]
    >  Um den obersten Interaktionsoperanden auszuwählen, dürfen Sie nicht zu nah am oberen Rand des kombinierten Fragments klicken.  
  
4.  Wächter. Sie können jeden Interaktionsoperanden mit einem Wächter versehen. Dieser beschreibt die Bedingung, unter der die Meldungen im Interaktionsoperanden ausgeführt werden.  
  
## <a name="creating-combined-fragments"></a>Erstellen von kombinierten Fragmenten  
 Eine Liste der Arten von Fragmenten, die Sie erstellen können, finden Sie unter [Arten von kombinierten Fragmenten](#KindsOfFragment).  
  
#### <a name="to-create-a-combined-fragment"></a>So erstellen Sie ein kombiniertes Fragment  
  
1. Wählen Sie eine Meldung oder eine Sequenz von Meldungen aus, die alle an der gleichen Lebenslinie oder Vorkommnisausführung beginnen.  
  
   > [!NOTE]
   >  Wenn Sie mehrere Meldungen auswählen, müssen diese eine ununterbrochene Sequenz bilden.  
  
2. Klicken Sie mit der rechten Maustaste auf eine der Meldungen, zeigen Sie auf **Umschließen mit**, und klicken Sie dann auf die gewünschte Art von kombiniertem Fragment, z. B. **Kombiniertes Alt-Fragment**.  
  
    Ein neues kombiniertes Fragment wird angezeigt. Die Überschrift gibt die Art von kombiniertem Fragment an, die Sie ausgewählt haben, z. B. **Alt**.  
  
    Im kombinierten Fragment befindet sich ein Fragment, das die ausgewählten Meldungen enthält.  
  
   Einigen Arten von kombinierten Fragmenten können weitere Interaktionsoperanden hinzugefügt werden.  
  
   Nachdem Sie Nachrichten in einem kombinierten Fragment neu angeordnet haben, wählen Sie im Kontextmenü die Option **Layout neu anordnen** aus, um die Größe des Rahmens des kombinierten Fragments zu ändern.  
  
#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>So fügen Sie einem kombinierten Fragment einen neuen Interaktionsoperanden hinzu  
  
1. Klicken Sie mit der rechten Maustaste im Interaktionsoperanden (2) auf eine leere Fläche, die sich außerhalb eines enthaltenen Fragments und unterhalb der Überschrift des kombinierten Fragments befindet.  
  
2. Zeigen Sie auf **Hinzufügen**.  
  
3. Klicken Sie auf **Interaktionsoperand vorher**oder **Interaktionsoperand nachher**.  
  
4. Sie können Meldungen im neuen Interaktionsoperanden hinzufügen, indem Sie die Meldungstools verwenden oder vorhandene Meldungen kopieren und einfügen.  
  
   Sie können die **Guard** -Eigenschaft eines Interaktionsoperanden festlegen, um die Bedingungen zu beschreiben, unter denen die darin enthaltenen Meldungen ausgeführt werden. In einem kombinierten **Loop** -Fragment können Sie den Wächter z. B. verwenden, um die Bedingung anzugeben, unter der die Schleife fortgesetzt wird. In einem kombinierten **Alt** -Fragment können Sie für jeden Interaktionsoperanden eine separate Bedingung angeben.  
  
#### <a name="to-set-the-guard-of-an-interaction-operand"></a>So legen Sie den Wächter eines Interaktionsoperanden fest  
  
1. Klicken Sie im Interaktionsoperanden (2) auf einen leeren Bereich außerhalb eines enthaltenen Fragments.  
  
    Um den Interaktionsoperanden und die Wächterbedingung herum wird ein Auswahlrahmen angezeigt.  
  
    Die Überschrift im Fenster **Eigenschaften** lautet **Interaktionsoperand**.  
  
2. Geben Sie die Wächterbedingung ein.  
  
    Die Bedingung wird am oberen Rand des Fragments (4) angezeigt.  
  
   Für einige Arten von kombinierten Fragmenten können die Eigenschaften festgelegt werden.  
  
#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>So legen Sie die Eigenschaften eines kombinierten Fragments fest oder zeigen diese an  
  
-   Klicken Sie mit der rechten Maustaste in den Titel des kombinierten Fragments, und klicken Sie dann auf **Eigenschaften**.  
  
    > [!NOTE]
    >  Verschiedene Arten von kombinierten Fragmenten verfügen über unterschiedliche Eigenschaften.  
  
##  <a name="KindsOfFragment"></a> Arten von kombinierten Fragmenten  
  
### <a name="fragments-describing-control-flow"></a>Fragmente, die die Ablaufsteuerung beschreiben  
 Ein einfaches Sequenzdiagramm zeigt nur eine typische Sequenz. Sie können die folgenden Typen von kombinierten Fragmenten verwenden, um Variationen zu beschreiben, die in unterschiedlichen Situationen auftreten können.  
  
|Fragmenttyp|Beschreibung|  
|-------------------|-----------------|  
|**Abonnieren**|Dies ist optional. Schließt eine Sequenz ein, die auftreten oder nicht auftreten kann. Im Wächter können Sie die Bedingung angeben, unter der die Sequenz auftritt.|  
|**ALT**|Enthält eine Liste von Fragmenten, die wiederum alternative Sequenzen von Meldungen enthalten. Es tritt nur jeweils eine Sequenz auf.<br /><br /> Sie können jedes Fragment mit einem Wächter versehen, um anzugeben, unter welcher Bedingung das Fragment ausgeführt werden kann. Der Wächter **else** gibt an, dass ein Fragment ausgeführt werden soll, wenn kein anderer Wächter den Wert „true“ hat. Wenn alle Wächter den Wert „false“ aufweisen und **else**nicht vorhanden ist, wird kein Fragment ausgeführt.|  
|**Loop**|Das Fragment wird einige Male wiederholt. Im Wächter können Sie die Bedingung angeben, unter der es wiederholt werden soll.<br /><br /> Kombinierte Loop-Fragmente haben die Eigenschaften **Min** und **Max**, die für den Mindest- und Höchstwert der Wiederholung des Fragments stehen. In der Standardeinstellung gilt keine Einschränkung.|  
|**Break**|Wenn dieses Fragment ausgeführt wird, wird der Rest der Sequenz verworfen. Im Wächter können Sie die Bedingung angeben, unter der die Unterbrechung eintritt.|  
|**Par**|Parallel Die Ereignisse in den Fragmenten können sich überlappen.|  
|**Kritisch**|Wird in einem Par- oder Seq-Fragment verwendet. Gibt an, dass die Meldungen in diesem Fragment sich nicht mit anderen Meldungen überlappen dürfen.|  
|**Seq**|Es sind zwei oder mehr Operandenfragmente vorhanden. Meldungen, die die gleiche Lebenslinie verwenden, müssen in der Reihenfolge der Fragmente auftreten. Falls Meldungen nicht die gleichen Lebenslinien verwenden, können sich Meldungen aus verschiedenen Fragmenten parallel überlappen.|  
|**Strict**|Es sind zwei oder mehr Operandenfragmente vorhanden. Die Fragmente müssen in der angegebenen Reihenfolge auftreten.|  
  
### <a name="fragments-about-how-to-interpret-the-sequence"></a>Fragmente zum Interpretieren der Sequenz  
 Standardmäßig gibt das Sequenzdiagramm eine Reihe von Meldungen an, die auftreten können. Im laufenden System können auch andere Meldungen auftreten, die Sie nicht für die Anzeige im Diagramm ausgewählt haben.  
  
 Die folgenden Fragmenttypen können verwendet werden, um diese Interpretation zu ändern.  
  
|Fragmenttyp|Beschreibung|  
|-------------------|-----------------|  
|**Betrachten Sie**|Gibt eine Liste der Meldungen an, die dieses Fragment beschreibt. Im laufenden System können andere Meldungen auftreten, die jedoch im Rahmen dieser Beschreibung nicht relevant sind.<br /><br /> Geben Sie die Liste in die **Messages** -Eigenschaft ein.|  
|**Ignorieren**|Eine Liste der Meldungen, die dieses Fragment nicht beschreibt. Diese Meldungen können im laufenden System auftreten, sind jedoch im Rahmen dieser Beschreibung nicht relevant.<br /><br /> Geben Sie die Liste in die **Messages** -Eigenschaft ein.|  
|**Assert**|Das Operandenfragment gibt die einzigen gültigen Sequenzen an. Wird in der Regel in einem Consider- oder Ignore-Fragment verwendet.|  
|**Neg**|Die in diesem Fragment angezeigte Sequenz darf nicht auftreten. Wird in der Regel in einem Consider- oder Ignore-Fragment verwendet.|  
  
## <a name="see-also"></a>Siehe auch  
 [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)   
 [Bearbeiten von UML-Modellen und -Diagrammen](../modeling/edit-uml-models-and-diagrams.md)



