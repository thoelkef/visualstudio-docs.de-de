---
title: 'Gewusst wie: Unterdrücken von Code Analyse Warnungen für generierten Code | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646273"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Gewusst wie: Unterdrücken von Codeanalysewarnungen für generierten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Compiler verwalteter Code generieren häufig Code, der einem Projekt hinzugefügt wird, um eine schnelle Code Entwicklung zu ermöglichen. Außerdem verwenden Entwickler häufig Tools von Drittanbietern, um Anwendungen schnell zu entwickeln. Diese Tools generieren außerdem Code, der dem Projekt hinzugefügt wird.

 Möglicherweise möchten Sie die Regel Verletzungen sehen, die von der Code Analyse in generiertem Code erkannt werden. Sie möchten Sie jedoch möglicherweise nicht anzeigen, wenn Sie den Code, der die Verletzung enthält, nicht anzeigen und verwalten können.

 Mithilfe des Kontrollkästchens **Ergebnisse aus generiertem Code unterdrücken** auf der Eigenschaften Seite Code Analyse eines Projekts können Sie auswählen, ob Code Analyse Warnungen von Code angezeigt werden sollen, der von einem Drittanbieter Tool generiert wurde.

> [!NOTE]
> Diese Option unterdrückt keine Code Analysefehler und-Warnungen aus generiertem Code, wenn die Fehler und Warnungen in Formularen und Vorlagen angezeigt werden. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>So unterdrücken Sie Warnungen für generierten Code in einem Projekt

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf **Codeanalyse**.

3. Aktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken** .
