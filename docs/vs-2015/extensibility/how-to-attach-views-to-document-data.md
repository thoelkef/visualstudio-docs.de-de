---
title: 'Vorgehensweise: Anfügen von Ansichten zu Dokumentdaten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bc1b57e189902624c13149d0264142ff66af050
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436004"
---
# <a name="how-to-attach-views-to-document-data"></a>Vorgehensweise: Anfügen von Ansichten zu Dokumentdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine neue Dokumentenansicht verfügen, können Sie ihn an ein vorhandenes dokumentendatenobjekt anfügen können.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Um festzustellen, ob eine Ansicht an ein vorhandenes dokumentendatenobjekt angefügt werden können  
  
1. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2. In der Implementierung von `IVsEditorFactory::CreateEditorInstance`, rufen Sie `QueryInterface` auf das vorhandene dokumentendatenobjekt, wenn die IDE aufruft Ihre `CreateEditorInstance` Implementierung.  
  
     Aufrufen von `QueryInterface` ermöglicht es Ihnen, die das vorhandene dokumentendatenobjekt, zu überprüfen, die im angegebenen die `punkDocDataExisting` Parameter.  
  
     Die genaue Schnittstellen, die Sie Abfragen ausführen müssen, jedoch hängt von den Editor, der das Dokument geöffnet wird wie in Schritt 4 beschrieben.  
  
3. Wenn Sie die entsprechenden Schnittstellen für das vorhandene dokumentendatenobjekt nicht finden können, geben Sie einen Fehlercode zurück, in-Editor, der angibt, dass das dokumentendatenobjekt nicht mit Ihrem Editor kompatibel ist.  
  
     In der IDE-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, ein Meldungsfeld benachrichtigt, wenn das Dokument in einem anderen Editor geöffnet ist und fragt, ob Sie sie schließen möchten.  
  
4. Wenn Sie in diesem Dokument schließen, ruft Visual Studio ein zweites Mal der Editorfactory. In diesem Aufruf die `DocDataExisting` Parameter gleich NULL ist. Die Implementierung der Factory-Editors kann dann das dokumentendatenobjekt in Ihren eigenen Editor öffnen.  
  
    > [!NOTE]
    > Bestimmt, ob Sie ein vorhandenes dokumentendatenobjekt arbeiten können, können Sie auch private Kenntnisse über die schnittstellenimplementierung durch Umwandeln der einen Zeiger auf die tatsächliche [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Klasse Ihrer privaten Implementierung. Alle standard-Editoren implementieren beispielsweise `IVsPersistFileFormat`, erbt von <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Sie können daher Aufrufen `QueryInterface` für <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, Klassen-ID und die Klassen-ID für das vorhandene dokumentendatenobjekt Ihrer Implementierung der übereinstimmt, und Sie das dokumentendatenobjekt arbeiten können.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn Visual Studio ruft die Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> -Methode es übergibt wieder einen Zeiger auf die vorhandenen dokumentendatenobjekts in der `punkDocDataExisting` -Parameters, sofern eine vorhanden ist. Überprüfen Sie das dokumentendatenobjekt zurückgegeben `punkDocDataExisting` zu bestimmen, ob das dokumentendatenobjekt geeignet, für den Editor, wie im Hinweis in Schritt 4 des Verfahrens in diesem Thema beschrieben ist. Wenn es eignet sich, Ihre Editorfactory sollte eine zweite Ansicht für die Daten bereitstellen, wie unter [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md). Wenn dies nicht der Fall ist, dann sollte eine entsprechende Fehlermeldung angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)
