---
title: Anzeigen von Dateien mit dem Befehl Open File | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cc24e259ac5aaa8526d5855a1662c146e1438ff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112155"
---
# <a name="display-files-by-using-the-open-file-command"></a>Anzeigen von Dateien mithilfe des Befehls Öffnen von Dateien
Die folgenden Schritte beschreiben, wie verarbeitet die IDE die **geöffnete Datei** Befehl, der verfügbar ist. die **Datei** im Menü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Die Schritte beschreiben außerdem, wie Projekte auf Aufrufe, die von diesem Befehl stammen, reagieren soll.

 Klickt ein Benutzer die **geöffnete Datei** Befehl die **Datei** im Menü und wählt aus einer Datei aus der **geöffnete Datei** im Dialogfeld der folgende Prozess durchgeführt:

1. Mithilfe der ausgeführten Dokumententabelle, bestimmt die IDE an, ob die Datei bereits in einem Projekt geöffnet ist.

    - Wenn die Datei geöffnet ist, auftritt die IDE das Fenster an.

    - Wenn die Datei nicht geöffnet ist, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Abfragen jedes Projekt, um zu bestimmen, welches Projekt die Datei öffnen kann.

        > [!NOTE]
        >  In der Projekt-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, geben Sie einen Prioritätswert, der die Stufe gibt an, an dem das Projekt die Datei geöffnet. Priority-Werte finden Sie in der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration.

2. Jedes Projekt gibt eine Prioritätsstufe, die die Wichtigkeit gibt an, es wird auf das Projekt die Datei geöffnet wird.

3. Die IDE verwendet die folgenden Kriterien, um zu bestimmen, welches Projekt die Datei geöffnet wird:

    - Das Projekt, das mit der höchsten Priorität reagiert (`DP_Intrinsic`) wird die Datei geöffnet. Wenn mehr als ein Projekt mit dieser Priorität antwortet, wird das erste Projekt, reagieren die Datei geöffnet.

    - Wenn kein Projekt mit der höchsten Priorität antwortet (`DP_Intrinsic`), aber alle Projekte mit der gleichen, niedriger Priorität, das aktive Projekt öffnet die Datei. Wenn kein Projekt aktiv ist, wird das erste Projekt, reagieren die Datei geöffnet.

    - Wenn kein Projekt mit den Besitz der Datei Ansprüche (`DP_Unsupported`), das Projekt verschiedene Dateien öffnet die Datei.

         Wenn eine Instanz des Projekts sonstige Dateien erstellt wird, wird das Projekt immer mit dem Wert antwortet `DP_CanAddAsExternal`. Dieser Wert gibt an, dass das Projekt die Datei öffnen kann. Dieses Projekt werden geöffnete Dateien enthalten, die nicht in anderen Projekten enthalten sind. Die Liste der Elemente in diesem Projekt wird nicht beibehalten; Dieses Projekt werden in **Projektmappen-Explorer** nur wenn er verwendet wird, eine Datei zu öffnen.

         Wenn das Projekt verschiedene Dateien nicht angegeben ist, dass die Datei geöffnet werden können, wurde eine Instanz des Projekts nicht erstellt. In diesem Fall wird die IDE erstellt eine Instanz des Projekts sonstige Dateien, und teilt dem Projekt die Datei geöffnet.

4. Sobald die IDE stellt fest, welches Projekt die Datei geöffnet wird, ruft der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode für das Projekt.

5. Das Projekt enthält dann die Möglichkeit, die Datei über einen projektspezifischen Editor oder einem standard-Editor zu öffnen. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md) und [Vorgehensweise: Öffnen Sie die standard-Editoren](../../extensibility/how-to-open-standard-editors.md)bzw.

## <a name="see-also"></a>Siehe auch
- [Anzeigen von Dateien mithilfe des Befehls Öffnen mit](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)
- [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)
- [Vorgehensweise: Open-standard-Editoren](../../extensibility/how-to-open-standard-editors.md)