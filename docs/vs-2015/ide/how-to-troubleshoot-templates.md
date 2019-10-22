---
title: 'Vorgehensweise: Problembehandlung bei Vorlagen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: acee84f582f2d6b8e2905e50db352cde794b73e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670604"
---
# <a name="how-to-troubleshoot-templates"></a>Gewusst wie: Problembehandlung bei Vorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn keine Vorlage in der Entwicklungsumgebung geladen werden kann, gibt es einige Möglichkeiten, das Problem zu erfassen.

## <a name="validating-the-vstemplate-file"></a>Überprüfen der VSTEMPLATE-Datei
 Wenn die VSTEMPLATE-Datei in einer Vorlage nicht dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Vorlagenschema folgt, wird die Vorlage möglicherweise nicht im Dialogfeld **Neues Projekt** angezeigt.

#### <a name="to-validate-the-vstemplate-file"></a>So überprüfen Sie die VSTEMPLATE-Datei

1. Suchen Sie die ZIP-Datei, die die Vorlage enthält.

2. Extrahieren Sie die ZIP-Datei.

3. Klicken Sie im Menü **Datei** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auf **Öffnen** und dann auf **Datei**.

4. Wählen Sie die VSTEMPLATE-Datei für die Vorlage aus, und klicken Sie auf **Öffnen**.

5. Stellen Sie sicher, dass das XML-Format der VSTEMPLATE-Datei dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Vorlagenschema folgt. Weitere Informationen zum VSTEMPLATE-Schema finden Sie in der [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Fügen Sie dem `VSTemplate`-Element ein `xmlns`-Attribut hinzu, und weisen Sie diesem den Wert http://schemas.microsoft.com/developer/vstemplate/2005 zu, um die IntelliSense-Unterstützung während der Erstellung der VSTEMPLATE-Datei zu nutzen.

6. Speichern und schließen Sie die VSTEMPLATE-Datei.

7. Wählen Sie die Dateien aus, die in Ihrer Vorlage enthalten sind, klicken Sie mit der rechten Maustaste auf diese, wählen Sie **Senden an** aus, und klicken Sie auf **ZIP-komprimierter Ordner**. Die ausgewählten Dateien werden in einer ZIP-Datei komprimiert.

8. Platzieren Sie die neue ZIP-Datei in demselben Verzeichnis, in dem sich auch die alte ZIP-Datei befand.

9. Löschen Sie die extrahierten Vorlagendateien und die alte ZIP-Datei der Vorlage.

## <a name="monitoring-the-event-log"></a>Überwachen des Ereignisprotokolls
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] protokolliert Fehler, die bei der Verarbeitung von ZIP-Vorlagendateien aufgetreten sind. Wenn eine Vorlage nicht wie erwartet im Dialogfeld **Neues Projekt** angezeigt wird, können Sie die **Ereignisanzeige** zur Behebung des Problems verwenden.

#### <a name="to-locate-template-errors-in-event-viewer"></a>So suchen Sie Vorlagenfehler in der Ereignisanzeige

1. Klicken Sie in Windows auf **Start** und **Systemsteuerung**, und doppelklicken Sie auf **Verwaltung** und dann auf **Ereignisanzeige**.

2. Klicken Sie im linken Bereich auf **Anwendung**.

3. Suchen Sie mit dem **Quellwert** `Visual Studio - VsTemplate` nach Ereignissen.

4. Doppelklicken Sie auf ein Vorlagenereignis, um den Fehler anzuzeigen.

## <a name="see-also"></a>Siehe auch
 [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md) [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md) [Schema Referenz zu Visual Studio](../extensibility/visual-studio-template-schema-reference.md) -Vorlagen
