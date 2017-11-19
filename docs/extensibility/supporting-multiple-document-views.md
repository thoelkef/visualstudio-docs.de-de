---
title: "Unterstützung mehrerer Dokumentansichten | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79b9224a16388dabbe2b68553e5c0d9bfff29519
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-multiple-document-views"></a>Unterstützung mehrerer Dokumentansichten
Sie können mehr als eine Ansicht eines Dokuments bereitstellen, indem Sie die Trennung der Dokumentdaten und Ansicht-Dokumentobjekte für den Editor erstellen. Einige Fälle, in denen ein zusätzlicher Dokumentenansicht sinnvoll wäre, sind:  
  
-   Unterstützung für neue Fenster:, damit ein Benutzer bereits ein Fenster im Editor zu öffnen, ein neues Fenster dazu öffnen kann, möchten Sie Ihren-Editor, um mindestens zwei Sichten des gleichen Typs ermöglichen die **neues Fenster** Befehl die **Fenster** Menü.  
  
-   Formular "und" Code anzeigen Unterstützung: Editor Ansichten verschiedener Typen bereitstellen sollen. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], enthält z. B. eine Formularansicht und eine Codeansicht.  
  
 Weitere Informationen hierzu finden Sie unter der CreateEditorInstance-Prozedur in der Datei EditorFactory.cs im benutzerdefinierten Editor-Projekt, das von der Visual Studio-Paketvorlage erstellt. Weitere Informationen zu diesem Projekt finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Synchronisieren von Ansichten  
 Wenn Sie mehrere Ansichten implementieren, ist das dokumentdatenobjekt verantwortlich für die Beibehaltung von allen Ansichten, die mit den Daten synchronisiert. Können Sie die Schnittstellen der Ereignisbehandlung auf <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> mehrere Ansichten mit den Daten zu synchronisieren.  
  
 Wenn Sie nicht verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt, das mehrere Ansichten synchronisiert, und klicken Sie dann Sie eigene Ereignissystem zum Behandeln der Änderungen an der dokumentdatenobjekt implementieren müssen. Verschiedene Ebenen der Granularität können Sie um mehrere Ansichten auf dem neuesten Stand zu halten. Während der Eingabe in einer Ansicht, werden zum Erstellen anderer Ansichten mit der Einstellung Maximale Granularität, sofort aktualisiert. Mit einer minimalen Granularität werden andere Sichten nicht aktualisiert, bis sie aktiviert sind.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Bestimmen, ob Dokumentdaten bereits geöffnet ist.  
 Die ausgeführten Document-Tabelle (RDT) in der integrierten Entwicklungsumgebung (IDE) hilft nachverfolgen, ob die Daten für ein Dokument bereits geöffnet ist, wie im folgenden Diagramm dargestellt.  
  
 ![Grafik zu DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Mehrere Ansichten  
  
 Standardmäßig befindet sich jede Ansicht (dokumentansichtsobjekts) in einem eigenen Fensterrahmen (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Wie bereits erwähnt können Daten jedoch in mehreren Ansichten angezeigt werden. Um dies zu ermöglichen, überprüft Visual Studio die RDT, um zu bestimmen, ob das betreffende Dokument bereits in einem Editor geöffnet ist. Wenn die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> um den Editor zu erstellen, ein Wert ungleich NULL zurückgegeben, der `punkDocDataExisting` Parameter gibt an, dass das Dokument bereits in einem anderen Editor geöffnet ist. Weitere Informationen dazu, wie die Funktionen RDT finden Sie unter [Document-Tabelle ausgeführt](../extensibility/internals/running-document-table.md).  
  
 In Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Implementierung, untersuchen Sie das dokumentdatenobjekt im zurückgegebenen `punkDocDataExisting` um zu bestimmen, ob die Daten für den Editor geeignet ist. (Z. B. sollte nur die HTML-Daten von einem HTML-Editor angezeigt werden.) Wenn es angebracht ist, sollten die Editorfactory eine zweite Ansicht für die Daten angeben. Wenn die `punkDocDataExisting` -Parameter ist kein `NULL`, es kann entweder, dass das dokumentdatenobjekt in einem anderen Editor geöffnet oder, wahrscheinlicher, dass die Daten bereits in einer anderen Ansicht mit der gleichen Editor geöffnet ist. Die Daten in einem anderen Editor geöffnet ist, die der Editorfactory nicht unterstützt, möglicherweise Visual Studio nicht Ihren Editorfactory-geöffnet. Weitere Informationen finden Sie unter [wie: Anfügen Ansichten der Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md).