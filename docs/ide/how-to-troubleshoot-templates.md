---
title: Problembehandlung beim Laden von Visual Studio-Projektvorlagen und -Elementvorlagen
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9242d053044fa66e6eb3d506382cf7cfb5d0295
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-troubleshoot-templates"></a>Vorgehensweise: Problembehandlung bei Vorlagen

Wenn keine Vorlage in der Entwicklungsumgebung geladen werden kann, gibt es einige Möglichkeiten, das Problem zu erfassen.

## <a name="validate-the-vstemplate-file"></a>Überprüfen der VSTEMPLATE-Datei

Wenn die VSTEMPLATE-Datei in einer Vorlage nicht dem Visual Studio-Vorlagenschema folgt, wird die Vorlage möglicherweise nicht im Dialogfeld **Neues Projekt** angezeigt.

### <a name="to-validate-the-vstemplate-file"></a>So überprüfen Sie die VSTEMPLATE-Datei

1. Suchen Sie die ZIP-Datei, die die Vorlage enthält.

1. Extrahieren Sie die ZIP-Datei.

1. Klicken Sie im Menü **Datei** in Visual Studio auf **Öffnen** > **Datei**.

1. Wählen Sie die VSTEMPLATE-Datei für die Vorlage aus, und klicken Sie auf **Öffnen**.

1. Stellen Sie sicher, dass das XML-Format der VSTEMPLATE-Datei dem Vorlagenschema folgt. Weitere Informationen zum VSTEMPLATE-Schema finden Sie unter [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Fügen Sie dem `VSTemplate`-Element ein `xmlns`-Attribut hinzu, und weisen Sie diesem einen Wert von „http://schemas.microsoft.com/developer/vstemplate/2005“ zu, um die IntelliSense-Unterstützung während der Erstellung der VSTEMPLATE-Datei zu nutzen.

1. Speichern und schließen Sie die VSTEMPLATE-Datei.

1. Wählen Sie die Dateien in Ihrer Vorlage aus, klicken Sie mit der rechten Maustaste, und klicken Sie auf **Senden an** > **ZIP-komprimierten Ordner**. Die ausgewählten Dateien werden in einer ZIP-Datei komprimiert.

1. Platzieren Sie die neue ZIP-Datei in demselben Verzeichnis, in dem sich auch die alte ZIP-Datei befand.

1. Löschen Sie die extrahierten Vorlagendateien und die alte ZIP-Datei der Vorlage.

## <a name="enable-diagnostic-logging"></a>Aktivieren der Diagnoseprotokollierung

Sie können die Diagnoseprotokollierung für die Ermittlung von Vorlagen aktivieren, indem Sie die Schritte unter [Troubleshooting template discovery (Extensibility) (Problembehandlung bei der Ermittlung von Vorlagen (Erweiterbarkeit))](../extensibility/troubleshooting-template-discovery.md) befolgen.

## <a name="see-also"></a>Siehe auch

[Troubleshooting template discovery (Extensibility) (Problembehandlung bei der Ermittlung von Vorlagen (Erweiterbarkeit))](../extensibility/troubleshooting-template-discovery.md)  
[Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)  
[Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)  
[Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)