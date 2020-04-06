---
title: Unterstützung mehrerer Dokumentansichten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699542"
---
# <a name="supporting-multiple-document-views"></a>Unterstützen mehrerer Dokumentansichten
Sie können mehr als eine Ansicht eines Dokuments bereitstellen, indem Sie separate Dokumentdaten und Dokumentansichtsobjekte für den Editor erstellen. Einige Fälle, in denen eine zusätzliche Dokumentansicht nützlich wäre, sind:

- Neue Fensterunterstützung: Sie möchten, dass Ihr Editor zwei oder mehr Ansichten desselben Typs angibt, sodass ein Benutzer, der bereits ein Fenster im Editor geöffnet hat, ein neues Fenster öffnen kann, indem er im Menü **Fenster** den Befehl **Neues Fenster** auswählt.

- Unterstützung für Formular- und Codeansicht: Sie möchten, dass der Editor Ansichten verschiedener Typen eingibt. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]stellt beispielsweise sowohl eine Formularansicht als auch eine Codeansicht bereit.

  Weitere Informationen hierzu finden Sie in der CreateEditorInstance-Prozedur in der EditorFactory.cs-Datei im benutzerdefinierten Editorprojekt, das von der Visual Studio-Paketvorlage erstellt wurde. Weitere Informationen zu diesem Projekt finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Synchronisieren von Ansichten
 Wenn Sie mehrere Ansichten implementieren, ist das Dokumentdatenobjekt dafür verantwortlich, dass alle Ansichten mit den Daten synchronisiert werden. Sie können die Ereignisbehandlungsschnittstellen <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> verwenden, um mehrere Ansichten mit den Daten zu synchronisieren.

 Wenn Sie das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt nicht zum Synchronisieren mehrerer Ansichten verwenden, müssen Sie ein eigenes Ereignissystem implementieren, um Änderungen am Dokumentdatenobjekt zu behandeln. Sie können verschiedene Granularitätsebenen verwenden, um mehrere Ansichten auf dem neuesten Stand zu halten. Mit einer Einstellung der maximalen Granularität, wie Sie in einer Ansicht eingeben, werden die anderen Ansichten sofort aktualisiert. Bei minimaler Granularität werden andere Ansichten erst aktualisiert, wenn sie aktiviert sind.

## <a name="determining-whether-document-data-is-already-open"></a>Bestimmen, ob Dokumentdaten bereits geöffnet sind
 Die laufende Dokumenttabelle (RDT) in der integrierten Entwicklungsumgebung (IDE) hilft dabei, nachzuverfolgen, ob die Daten für ein Dokument bereits geöffnet sind, wie im folgenden Diagramm dargestellt.

 ![DocDataView-Grafik](../extensibility/media/docdataview.gif "Docdataview") Mehrere Ansichten

 Standardmäßig ist jede Ansicht (Dokumentansichtsobjekt) in einem<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>eigenen Fensterrahmen ( ) enthalten. Wie bereits erwähnt, können Dokumentdaten jedoch in mehreren Ansichten angezeigt werden. Um dies zu ermöglichen, überprüft Visual Studio die RDT, um festzustellen, ob das betreffende Dokument bereits in einem Editor geöffnet ist. Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> IDE aufruft, den Editor zu erstellen, gibt ein im `punkDocDataExisting` Parameter zurückgegebener Wert für nicht NULL an, dass das Dokument bereits in einem anderen Editor geöffnet ist. Weitere Informationen zur Funktionsweise der RDT finden Sie unter Ausführen der [Dokumenttabelle](../extensibility/internals/running-document-table.md).

 Untersuchen <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Sie in der Implementierung das `punkDocDataExisting` zurückgegebene Dokumentdatenobjekt, um festzustellen, ob die Dokumentdaten für den Editor geeignet sind. (Z. B. sollten nur HTML-Daten von einem HTML-Editor angezeigt werden.) Wenn dies angebracht ist, sollte Ihre Editorfactory eine zweite Ansicht für die Daten bereitstellen. Wenn `punkDocDataExisting` der Parameter `NULL`nicht ist, ist es möglich, dass entweder das Dokumentdatenobjekt in einem anderen Editor geöffnet ist, oder, wahrscheinlicher, dass die Dokumentdaten bereits in einer anderen Ansicht mit demselben Editor geöffnet sind. Wenn die Dokumentdaten in einem anderen Editor geöffnet sind, den Ihre Editorfactory nicht unterstützt, kann Visual Studio die Editorfactory nicht öffnen. Weitere Informationen finden Sie unter [Gewusst wie: Anfügen von Ansichten an Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md).
