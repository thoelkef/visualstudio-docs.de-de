---
title: "Unterst&#252;tzung mehrerer Dokumentansichten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] benutzerdefinierte - mehrere Dokumentansichten"
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Unterst&#252;tzung mehrerer Dokumentansichten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können mehr als eine Ansicht eines Dokuments durch das Erstellen von separaten Dokumenten von Daten und Objekte der Dokumente für den Editor bereitstellen.  Einige zusätzliche Fälle, in denen eine Ansicht des Dokuments nützlich wäre, sind:  
  
-   Unterstützung des neuen Fensters: Sie möchten, dass der Editor mindestens zwei Ansichten des gleichen Typs bereitstellen, damit ein Benutzer, der bereits ein Fenster, das im Editor geöffnet ist, wird ein neues Fenster geöffnet werden kann, indem der **Neues Fenster** Befehl aus dem Menü **Fenster** auswählt.  
  
-   Codeansichts Formular und die Unterstützung: Sie möchten, dass der Editor Sichten unterschiedlicher Typen bereitstellen.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]zum Beispiel wird eine Formularansicht und eine Codeansicht.  
  
 Weitere Informationen hierzu finden Sie unter CreateEditorInstance\-Prozedur in der EditorFactory.cs\-Datei im benutzerdefinierten Editor, das von der Visual Studio\-Paket\-Vorlage erstellt wird.  Weitere Informationen über dieses Projekt finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## Ansichten synchronisieren  
 Wenn Sie mehrere Ansichten implementieren, ist das Dokument das angegebene Channeldatenobjekt zum Beibehalten aller Ansichten synchronisiert mit den Daten zuständig.  Sie können die Schnittstellen für die Ereignisbehandlung <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> verwenden, um mehrere Ansichten mit den Daten zu synchronisieren.  
  
 Wenn Sie nicht das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\-Objekt verwenden, um mehrere Ansichten zu synchronisieren, müssen Sie implementieren, Ereignissystem besitzen, um die Änderungen zu verarbeiten, die an das angegebene Channeldatenobjekt Dokument vorgenommen werden.  Sie können verschiedene Ebenen der Granularität verwenden, um mehrere Ansichten auf dem neuesten Stand zu halten.  Mit der Einstellung der Eigenschaft Maximale Granularität, wie Sie eine Sicht eingeben, werden andere Ansichten gleichzeitig aktualisiert werden.  Arbeiten mit minimaler Granularität werden andere Sichten nicht aktualisiert, wenn sie aktiviert sind.  
  
## Bestimmen, ob Dokumenten\-Bezugspunkte bereits geöffnet ist  
 Die aktive Dokument \(Drehtransformator\) in Hilfe Bildlaufziehleiste der integrierten Entwicklungsumgebung \(IDE\), ob die Daten für ein Dokument bereits geöffnet ist, wie im folgenden Diagramm dargestellt.  
  
 ![Grafik zu DocDataView](../extensibility/media/docdataview.png "Docdataview")  
Mehrere Ansichten  
  
 Standardmäßig wird jede Ansicht \(Objekt\) der Dokumente in einem eigenen Fensterrahmen \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>\) enthalten.  Wie bereits erwähnt, kann jedoch Dokumentdaten in mehreren Ansichten angezeigt werden.  Um dies zu aktivieren, überprüft Visual Studio den Drehtransformator um zu bestimmen, ob das Dokument, das fragliche wurde bereits in einem Editor geöffnet ist.  Wenn die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> aufruft, um den Editor zu erstellen, gibt ein Werter ungleicher NULL, der im `punkDocDataExisting`\-Parameter zurückgegeben wurde, wird das Dokument bereits in einem anderen Editor geöffnet ist.  Weitere Informationen darüber, wie der Drehtransformator finden Sie unter [Dokumenttabelle der ausgeführten](../extensibility/internals/running-document-table.md).  
  
 In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Implementierung überprüfen Sie das Dokument das angegebene Channeldatenobjekt, das in `punkDocDataExisting` zurückgegeben wird, um festzustellen, ob die Dokumentdaten für den Editor geeignet ist.  \(Zum Beispiel nur HTML\-Bezugspunkte sollten durch einen HTML\-Editor angezeigt werden.\) Wenn es angemessen ist, sollte der Editor factory eine zweite Sicht für die Daten bereitstellen.  Wenn der Parameter nicht `punkDocDataExisting``NULL`ist, ist er entweder, dass das Dokument das angegebene Channeldatenobjekt in einem anderen Editor geöffnet ist oder möglich, wahrscheinlicher, dass die Dokumentdaten bereits in einer anderen Ansicht mit gleichen der Editor geöffnet ist.  Wenn die Dokumentdaten in einem anderen Editor geöffnet ist, den der Editor factory nicht unterstützt, kann der Editor factory nicht öffnen.  Weitere Informationen finden Sie unter [Gewusst wie: Anfügen von Ansichten, um Daten](../extensibility/how-to-attach-views-to-document-data.md).