---
title: Problembehandlung beim Laden von Projekt- und Elementvorlagen
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2b3a94ab9a44776b0c6716b99f594ec0fd840938
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943414"
---
# <a name="how-to-troubleshoot-templates"></a>Vorgehensweise: Problembehandlung bei Vorlagen

Wenn keine Vorlage in der Entwicklungsumgebung geladen werden kann, gibt es einige Möglichkeiten, das Problem zu erfassen.

## <a name="validate-the-vstemplate-file"></a>Überprüfen der VSTEMPLATE-Datei

Wenn die *VSTEMPLATE*-Datei in einer Vorlage nicht dem Visual Studio-Vorlagenschema folgt, wird die Vorlage möglicherweise nicht im Dialogfeld **Neues Projekt** angezeigt.

### <a name="to-validate-the-vstemplate-file"></a>So überprüfen Sie die VSTEMPLATE-Datei

1. Suchen Sie die *ZIP*-Datei, die die Vorlage enthält.

1. Extrahieren Sie die *ZIP*-Datei.

1. Klicken Sie im Menü **Datei** in Visual Studio auf **Öffnen** > **Datei**.

1. Wählen Sie die *VSTEMPLATE*-Datei für die Vorlage aus, und klicken Sie auf **Öffnen**.

1. Stellen Sie sicher, dass das XML-Format der *VSTEMPLATE*-Datei dem Vorlagenschema folgt. Weitere Informationen zum *VSTEMPLATE*-Schema finden Sie unter [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Fügen Sie dem `VSTemplate`-Element ein `xmlns`-Attribut hinzu, und weisen Sie diesem einen Wert von http://schemas.microsoft.com/developer/vstemplate/2005 zu, um die IntelliSense-Unterstützung während der Erstellung der *VSTEMPLATE*-Datei zu nutzen.

1. Speichern und schließen Sie die *VSTEMPLATE*-Datei.

1. Wählen Sie die Dateien in Ihrer Vorlage aus, klicken Sie mit der rechten Maustaste, und klicken Sie auf **Senden an** > **ZIP-komprimierten Ordner**. Die ausgewählten Dateien werden in eine *ZIP*-Datei komprimiert.

1. Platzieren Sie die neue *ZIP*-Datei in dem Verzeichnis, in dem sich auch die alte *ZIP*-Datei befand.

1. Löschen Sie die extrahierten Vorlagendateien und die alte *ZIP*-Datei der Vorlage.

## <a name="enable-diagnostic-logging"></a>Aktivieren der Diagnoseprotokollierung

Sie können die Diagnoseprotokollierung für die Ermittlung von Vorlagen aktivieren, indem Sie die Schritte unter [Troubleshooting template discovery (Extensibility) (Problembehandlung bei der Ermittlung von Vorlagen (Erweiterbarkeit))](../extensibility/troubleshooting-template-discovery.md) beschrieben befolgen.

## <a name="see-also"></a>Siehe auch

- [Troubleshooting template discovery (Extensibility) (Problembehandlung bei der Ermittlung von Vorlagen (Erweiterbarkeit))](../extensibility/troubleshooting-template-discovery.md)
- [Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)