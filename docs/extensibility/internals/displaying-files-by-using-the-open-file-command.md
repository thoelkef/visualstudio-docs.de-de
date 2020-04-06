---
title: Anzeigen von Dateien mithilfe des Befehls "Datei öffnen" | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708600"
---
# <a name="display-files-by-using-the-open-file-command"></a>Anzeigen von Dateien mithilfe des Befehls Datei öffnen
Die folgenden Schritte beschreiben, wie die IDE den Befehl **Datei** öffnen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verarbeitet, der im Menü **Datei** in verfügbar ist. In den Schritten wird auch beschrieben, wie Projekte auf Aufrufe reagieren sollen, die von diesem Befehl stammen.

 Wenn ein Benutzer im Menü **Datei** auf den Befehl **Datei** öffnen klickt und eine Datei aus dem Dialogfeld **Datei öffnen** auswählt, tritt der folgende Vorgang auf:

1. Anhand der laufenden Dokumenttabelle bestimmt die IDE, ob die Datei bereits in einem Projekt geöffnet ist.

    - Wenn die Datei geöffnet ist, wird das Fenster von der IDE erneut angezeigt.

    - Wenn die Datei nicht geöffnet <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> ist, ruft die IDE jedes Projekt auf, um zu bestimmen, welches Projekt die Datei öffnen kann.

        > [!NOTE]
        > Geben Sie in <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>der Projektimplementierung von einen Prioritätswert an, der die Ebene angibt, auf der das Projekt die Datei öffnet. Prioritätswerte werden <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> in der Enumeration bereitgestellt.

2. Jedes Projekt antwortet mit einer Prioritätsstufe, die angibt, wie wichtig es ist, das Projekt zum Öffnen der Datei zu sein.

3. Die IDE verwendet die folgenden Kriterien, um zu bestimmen, welches Projekt die Datei öffnet:

    - Das Projekt, das mit der`DP_Intrinsic`höchsten Priorität ( ) antwortet, öffnet die Datei. Wenn mehr als ein Projekt mit dieser Priorität antwortet, öffnet das erste zu beantwortende Projekt die Datei.

    - Wenn kein Projekt mit der`DP_Intrinsic`höchsten Priorität ( ) antwortet, aber alle Projekte mit der gleichen, niedrigeren Priorität antworten, öffnet das aktive Projekt die Datei. Wenn kein Projekt aktiv ist, wird die Datei vom ersten zu beantwortenden Projekt geöffnet.

    - Wenn kein Projekt den Besitz`DP_Unsupported`der Datei ( beansprucht , öffnet das Projekt Verschiedene Dateien die Datei.

         Wenn eine Instanz des Projekts Verschiedene Dateien erstellt wird, antwortet das `DP_CanAddAsExternal`Projekt immer mit dem Wert . Dieser Wert gibt an, dass das Projekt die Datei öffnen kann. Dieses Projekt wird verwendet, um offene Dateien zu speichern, die sich in keinem anderen Projekt befinden. Die Liste der Elemente in diesem Projekt wird nicht beibehalten. Dieses Projekt ist im **Projektmappen-Explorer** nur sichtbar, wenn es zum Öffnen einer Datei verwendet wird.

         Wenn das Projekt Verschiedene Dateien nicht darauf hinweist, dass es die Datei öffnen kann, wurde keine Instanz des Projekts erstellt. In diesem Fall erstellt die IDE eine Instanz des Projekts Verschiedene Dateien und weist das Projekt an, die Datei zu öffnen.

4. Sobald die IDE bestimmt, welches Projekt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Datei öffnet, ruft sie die Methode für dieses Projekt auf.

5. Das Projekt hat dann die Möglichkeit, die Datei mit einem projektspezifischen Editor oder einem Standardeditor zu öffnen. Weitere Informationen finden Sie unter [Gewusst wie: Öffnen projektspezifischer Editoren](../../extensibility/how-to-open-project-specific-editors.md) [bzw. How to: Open standard editors.](../../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>Weitere Informationen
- [Anzeigen von Dateien mithilfe des Befehls "Mit öffnen"](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)
- [Gewusst wie: Öffnen sie projektspezifische Editoren](../../extensibility/how-to-open-project-specific-editors.md)
- [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
