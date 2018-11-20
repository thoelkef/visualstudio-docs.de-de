---
title: Unterstützen mehrerer Dokumentansichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6be1e48917c8ad5e7035f01caa4f74b78a6fa3d0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792254"
---
# <a name="supporting-multiple-document-views"></a>Unterstützen mehrerer Dokumentansichten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mehr als eine Ansicht eines Dokuments angeben, durch die Trennung der Dokumentdaten und dokumentenansichtsobjekten für den Editor erstellen. Einige Fälle, in denen ein zusätzlicher Dokumentenansicht sinnvoll wäre, sind:  
  
- Unterstützung für das neue Fenster: sollen Ihre-Editor, um mindestens zwei Ansichten des gleichen Typs enthalten, ein Benutzer, der bereits ein Fenster im Editor geöffnet hat ein neues Fenster, die sich durch Auswählen öffnen kann der **neues Fenster** Befehl die **Fenster** Menü.  
  
- Form "und" Code anzeigen Unterstützung: Sie möchten Ihre-Editor, um die Ansichten für verschiedene Arten bereitstellen. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], z. B. bietet sowohl eine Formularansicht und eine Codeansicht.  
  
  Weitere Informationen hierzu finden Sie im Verfahren "CreateEditorInstance" in der Datei EditorFactory.cs im benutzerdefinierten Editor-Projekt, das von der Visual Studio-Paketvorlage erstellt. Weitere Informationen zu diesem Projekt finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Ansichten werden synchronisiert  
 Wenn Sie mehrere Ansichten implementieren, ist das dokumentendatenobjekt selbst dafür verantwortlich, alle Ansichten, die mit den Daten synchron. Können Sie die Ereignisbehandlung-Schnittstellen auf <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> mehrere Ansichten mit den Daten zu synchronisieren.  
  
 Wenn Sie nicht verwenden, die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt, das mehrere Ansichten, synchronisiert, und klicken Sie dann Sie Ihr eigenes Ereignissystem zum Verarbeiten von Änderungen an das dokumentendatenobjekt implementieren müssen. Sie können verschiedene Ebenen der Granularität verwenden, um mehrere Ansichten auf dem neuesten Stand zu halten. Während der Eingabe in einer Ansicht, werden die anderen Ansichten mit der Einstellung höchstmögliche Granularität, sofort aktualisiert. Mit minimalen Granularität sind andere Sichten nicht aktualisiert, bis sie aktiviert werden.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Bestimmen, ob die Daten Dokument bereits geöffnet ist.  
 Der ausgeführten Dokumententabelle (RDT) in der integrierten Entwicklungsumgebung (IDE) kann nachzuverfolgen, ob die Daten für ein Dokument bereits geöffnet ist, wie im folgenden Diagramm dargestellt.  
  
 ![Grafik zu DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Mehrere Ansichten  
  
 Standardmäßig ist jeder Ansicht (dokumentenansichtsobjekt) in eine eigene Fensterrahmen enthalten (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Wie bereits erwähnt können Dokumentdaten jedoch in mehreren Ansichten angezeigt werden. Um dies zu ermöglichen, überprüft Visual Studio den RDT an, um zu bestimmen, ob das betreffende Dokument bereits in einem Editor geöffnet ist. Wenn die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ein Wert ungleich NULL zurückgegeben, um den Editor zu erstellen, in der `punkDocDataExisting` Parameter gibt an, dass das Dokument bereits in einem anderen Editor geöffnet ist. Weitere Informationen zur Verwendung die RDT-Funktionen finden Sie unter [Running Document Table](../extensibility/internals/running-document-table.md).  
  
 In Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Implementierung, untersuchen Sie das dokumentendatenobjekt im zurückgegebenen `punkDocDataExisting` zu bestimmen, ob die Dokumentendaten für den Editor geeignet ist. (Zum Beispiel sollte nur HTML-Daten von einem HTML-Editor angezeigt werden.) Wenn dies sinnvoll ist, sollte der Editorfactory eine zweite Ansicht für die Daten bereitstellen. Wenn die `punkDocDataExisting` -Parameter ist kein `NULL`, es kann entweder, dass das dokumentendatenobjekt in einem anderen Editor geöffnet oder, wahrscheinlicher ist, die Daten bereits in einer anderen Ansicht mit gleichen Editor geöffnet ist. Wenn die Dokumentdaten in einem anderen Editor geöffnet, die der Editorfactory nicht unterstützt ist, schlägt Visual Studio zu Ihrem-Editor-Factory zu öffnen. Weitere Informationen finden Sie unter [Vorgehensweise: Anfügen von Ansichten zu Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md).

