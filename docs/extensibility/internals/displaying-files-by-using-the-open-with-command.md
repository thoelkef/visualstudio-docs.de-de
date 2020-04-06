---
title: Anzeigen von Dateien mithilfe des Befehls Öffnen mit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708581"
---
# <a name="display-files-by-using-the-open-with-command"></a>Anzeigen von Dateien mithilfe des Befehls "Mit öffnen"
Ein Projekt kann die IDE auffordern, das Dialogfeld **Öffnen mit** anzuzeigen. Diese Anforderung fordert den Benutzer auf, eine Datei mit einer Auswahl an Standard-Editoren zu öffnen. Die folgenden Schritte beschreiben diesen Prozess:

1. Das Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>ruft auf, `OSE_UseOpenWithDialog` und `OSEOpenDocEditor` gibt einen Wert von für den Parameter an.

2. Basierend auf der Dateinamenerweiterung des Dokuments bestimmt die IDE, welche in der Registrierung aufgeführten Editoren das angegebene Dokument öffnen können, und zeigt diese Informationen im Dialogfeld **Öffnen** mit an.

    > [!NOTE]
    > Projekte mit einem intrinsischen Editor, die in das Dialogfeld **"Mit öffnen"** aufgenommen werden müssen, müssen für jeden dieser Editoreine eine Editorfactory registrieren. Intrinsische Editoren funktionieren nur zusammen mit einem bestimmten <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Projekttyp, der bei der Implementierung der Methode erzwungen wird. Die IDE verfügt über eine integrierte Editorfactory für den Kerntexteditor und den Binäreditor. Die IDE erstellt auch eine Instanz einer Editorfactory im Namen jeder registrierten Windows-Dateizuordnung. Ein Beispiel für eine solche Datei ist Microsoft Word.

3. Sobald der Benutzer ein Element aus dem Dialogfeld **"Mit öffnen"** auswählt, öffnet die IDE das Dokument dann durch Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> der Methode. Weitere Informationen finden Sie unter [Gewusst wie: Öffnen von Standardeditoren](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Weitere Informationen
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)
- [Anzeigen von Dateien mithilfe des Befehls Datei öffnen](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
