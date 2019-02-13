---
title: Melden eines Problems mit Visual Studio
titleSuffix: ''
description: Erfahren Sie, wie Sie ein Problem mit Visual Studio 2017 an Microsoft melden, sodass wir eine Diagnose durchführen und das Problem beheben können.
ms.date: 03/11/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e9ce21c0abf365606b1c09aa37c59e4217feb02
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936927"
---
# <a name="how-to-report-a-problem-with-visual-studio-2017"></a>Melden eines Problems mit Visual Studio 2017

Wenn ein Problem mit Visual Studio auftritt, möchten wir dies erfahren. So melden Sie das Problem auf der [Developer Community](https://developercommunity.visualstudio.com/)-Website, damit wir eine Diagnose durchführen und uns um die Behebung kümmern können.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter[Melden eines Problems in Visual Studio für Mac](/visualstudio/mac/report-a-problem).

## <a name="report-a-problem-by-using-visual-studio"></a>Melden eines Problems mithilfe von Visual Studio

Wenn Sie ein Problem mit Visual Studio melden möchten, müssen Sie den Bericht in Visual Studio oder im Visual Studio-Installer initiieren. Direkt über die [Developer Community](https://developercommunity.visualstudio.com/)-Website ist dies nicht möglich. Erfolgt die Berichterstattung über Visual Studio, sind die Diagnoseinformationen automatisch im Bericht enthalten.

![Popupelement „Problem melden“ auf der Visual Studio Developer Community-Website](media/report-an-issue.png)

1. Wählen Sie in Visual Studio **Hilfe** > **Feedback senden** > **Problem melden** aus.

   > [!TIP]
   > Wenn Sie die Installation von Visual Studio nicht abschließen oder nicht auf das Feedbacktool in Visual Studio zugreifen können, können Sie über den **Visual Studio-Installer** ein Problem melden. Klicken Sie hierfür in der rechten oberen Ecke des **Visual Studio-Installers** auf das Feedbacksymbol.

1. Wenn Sie nicht angemeldet sind, wählen Sie auf der rechten Seite des Tools **Anmelden** aus, wie im folgenden Screenshot gezeigt. Befolgen Sie die Anweisungen auf dem Bildschirm für die Anmeldung.

   ![Anmelden zum Melden eines Problems](../ide/media/sign-in-new-ux.png)

   Wenn Sie sich anmelden, können Sie ein Problem melden und für gepostete Probleme abstimmen oder sie kommentieren.

1. Nach der Anmeldung werden Ihnen auf dem Bildschirm **Elemente, denen ich folge** die Bereiche **Probleme** und **Aktivität** angezeigt.

    ![Elemente, denen ich folge](../ide/media/items-i-follow.png)

1. Visual Studio stellt eine Schnittstelle bereit, über die Sie nach Ihrem Problem suchen und überprüfen können, ob andere es bereits gemeldet haben. Wenn es bereits gemeldet wurde, stimmen Sie dafür, um uns zu informieren.
   > [!NOTE]
   > Eine Suchanfragen lässt sich ausführen, indem Sie den gewünschten Text in das Suchfeld eingeben und entweder auf die EINGABETASTE drücken oder auf das Suchsymbol klicken.

   ![Ähnliche Probleme suchen und für sie abstimmen](../ide/media/search-and-vote.png)

1. Wenn Sie das gesuchte Problem nicht finden, klicken Sie am unteren Rand des Bildschirms auf **Neues Problem melden**.

   > [!NOTE]
   > Die Schaltfläche **Neues Problem melden** ist nur in der Developer Community-Schnittstelle in Visual Studio verfügbar. Probleme können nicht direkt auf der [Developer Community](https://developercommunity.visualstudio.com/)-Website gemeldet werden.

1. Geben Sie einen aussagekräftigen Titel für das Problem an, der uns die Weiterleitung an das richtige Visual Studio-Team erleichtert.

1. Geben Sie zusätzliche Details und, wenn möglich, die Schritte zum Reproduzieren des Problems an.

   ![Neues Problem melden](../ide/media/report-new-problem.png)

1. Klicken Sie auf **Weiter**, um zur Registerkarte **Anlagen** zu wechseln. Hier können Sie einen Screenshot machen, um ihn später an Microsoft zu senden. Wenn Sie weitere Screenshots oder andere Dateien anfügen möchten, klicken Sie auf **Weitere Dateien anfügen**.

   ![Screenshot zu einem Visual Studio-Problembericht hinzufügen](media/report-a-problem-screenshot.png)

1. Wenn Sie keinen Screenshot anfügen oder keine [Reproduktion aufzeichnen](#record-a-repro) möchten, klicken Sie auf **Weiter**, um zur Registerkarte **Zusammenfassung** zu wechseln.

1. Klicken Sie auf die Schaltfläche **Absenden**, um den Bericht zusammen mit allen Bildern, Ablaufverfolgungs- und Abbilddateien zu senden. (Wenn die Schaltfläche **Senden** grau dargestellt ist, überprüfen Sie, ob Sie einen Titel und eine Beschreibung für den Bericht eingegeben haben.)

   Informationen zu den erfassten Daten finden Sie unter [Data we collect (Daten, die wir erfassen)](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Aufnehmen einer Reproduktion

Ablaufverfolgungs- und Heap-Abbilddateien sind nützlich für die Diagnose von Problemen. Verwenden Sie gerne das Tool **Problem melden**, um die Schritte zum Reproduzieren des Problems zu erfassen und die Daten an Microsoft zu senden. Gehen Sie dabei so vor:

1. Nachdem Sie einen Titel und eine Beschreibung für Ihr Problem eingegeben haben, klicken Sie auf **Weiter**, um zur Registerkarte **Anlagen** zu wechseln.

1. Klicken Sie auf die Registerkarte **Datensatz**.

1. Wählen Sie unter **Zeichnen Sie Ihre Aktionen auf** die aktuelle Visual Studio-Instanz aus, wenn Sie das Problem dort reproduzieren können. Falls dies nicht der Fall ist, z.B. weil Visual Studio abgestürzt ist, klicken Sie auf **\<Create a new instance>** (<Neue Instanz erstellen>), um die Aktionen in einer neuen Visual Studio-Instanz aufzuzeichnen.

1. Klicken Sie auf **Aufzeichnung starten**. Erteilen Sie die Berechtigung zum Ausführen des Tools.

   ![Auf „Aufzeichnung starten“ klicken, um eine Ablaufverfolgungs- und eine Heapabbilddatei in einem Visual Studio-Problembericht bereitzustellen](../ide/media/record-dialog-box.png)

1. Wenn das Tool **Problemaufzeichnung** angezeigt wird, führen Sie die Schritte zum Reproduzieren des Problems aus.

1. Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **Stop Record** (Aufzeichnung beenden).

1. Warten Sie einige Minuten, bis Visual Studio die aufgezeichneten Informationen erfasst und gepackt hat.

   Informationen zu den erfassten Daten finden Sie unter [Data we collect (Daten, die wir erfassen)](developer-community-privacy.md#data-we-collect).

## <a name="when-further-information-is-needed-need-more-info"></a>Wann sind weitere Informationen erforderlich? (Weitere Informationen erforderlich)

Ab Visual Studio 2017-Version 15.5 gibt es einen neuen Workflow, mit dem Benutzer zusätzliche Informationen über Problemberichte bereitstellen können.

1. Wenn ein Microsoft-Techniker ein Problem auf der Website [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) auf den Status **Weitere Informationen erforderlich** festlegt, erhalten der Benutzer, der das Problem veröffentlicht hat, und alle, die dafür abgestimmt haben, ihm folgen oder es kommentiert haben, eine Benachrichtigung im Tool **Problem melden** in Visual Studio.

   ![Benachrichtigung „Weitere Informationen erforderlich“ in Visual Studio](../ide/media/nmi-notification.png)

1. Klicken Sie auf den Link **Probleme anzeigen**, um die Ansicht der Probleme, die Ihre Aufmerksamkeit erfordern, zu filtern und zu sortieren. Diese Probleme wurden mit einem Indikator versehen, über den sie in der allgemeinen Suche unterschieden werden können.

1. Klicken Sie auf ein Problem, um die Problemdetails anzuzeigen.

   ![Benachrichtigung „Weitere Informationen erforderlich“](../ide/media/nmi-details-view.png)

1. Wenn Sie die Anforderung **Weitere Informationen erforderlich** anzeigen möchten, klicken Sie auf den Link **Anforderung anzeigen und antworten** in der Detailansicht des Problems. Die Anforderung wird in einem Dialogfeld angezeigt.

   ![Benachrichtigung „Weitere Informationen erforderlich“](../ide/media/nmi-request.png)

1. Sie können durch das Hinzufügen von Kommentaren oder Anlagen und das Aufzeichnen von Schritten weitere Informationen bereitstellen. Dies funktioniert ähnlich wie das Melden neuer Probleme oder das Bereitstellen zusätzlicher Informationen beim Abstimmen für ein Problem.

1. Der anfordernde Microsoft-Techniker empfängt eine Benachrichtigung über die bereitgestellten zusätzlichen Informationen. Wenn sie über ausreichend Informationen verfügen, um das Problem zu untersuchen, wird der Problemstatus geändert. Anderenfalls fordert der Techniker erneut weitere Informationen an.

   > [!NOTE]
   > * Wenn Sie antworten, verschwindet die Benachrichtigung. Stattdessen sehen Sie ein Dankeschön-Banner, über das Sie weitere Informationen bereitstellen können.
   > * Nachdem sich der Status des Problems geändert hat, verschwindet die Benachrichtigung für alle Benutzer, die dem Problem folgen.
   > * Mehr als eine Person kann auf dieselbe **Weitere Informationen erforderlich**-Anforderung antworten.
   > * Auf der [Developer Community](https://developercommunity.visualstudio.com/)-Website gibt es keinen Workflow namens **Weitere Informationen erforderlich**, wenn Sie direkt über einen Webbrowser darauf zugreifen. Sie können dort jedoch kommentieren und Anlagen hochladen.

## <a name="search-for-solutions-or-provide-feedback"></a>Suchen nach Lösungen oder Geben von Feedback

Wenn Sie ein Problem nicht über Visual Studio melden möchten oder können, wurde es möglicherweise bereits gemeldet und eine Lösung auf der Website [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) veröffentlicht.

Wenn Sie kein Problem melden, sondern ein Feature vorschlagen möchten, haben Sie auch hierzu die Möglichkeit. Weitere Informationen finden Sie auf der Seite [Suggest a feature (Vorschlagen eines Features)](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="see-also"></a>Siehe auch

* [Sprechen Sie mit uns](../ide/talk-to-us.md)
* [Vorgehensweise: Melden eines Problems mit Visual Studio für Mac](/visualstudio/mac/report-a-problem)
* [Melden eines Problems mit dem Visual C++-Toolset oder der -Dokumentation](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Developer Community](https://developercommunity.visualstudio.com/)
* [Developer Community data privacy (Datenschutz in der Entwicklercommunity)](developer-community-privacy.md)