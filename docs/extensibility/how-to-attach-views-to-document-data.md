---
title: 'Gewusst wie: Anfügen von Ansichten an Dokumentdaten | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711093"
---
# <a name="how-to-attach-views-to-document-data"></a>Gewusst wie: Anfügen von Ansichten zu Dokumentdaten
Wenn Sie über eine neue Dokumentansicht verfügen, können Sie sie möglicherweise an ein vorhandenes Dokumentdatenobjekt anfügen.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>So ermitteln Sie, ob Sie eine Ansicht an ein vorhandenes Dokumentdatenobjekt anfügen können

1. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Rufen Sie `IVsEditorFactory::CreateEditorInstance`in `QueryInterface` ihrer Implementierung von das vorhandene Dokumentdatenobjekt auf, wenn die IDE Ihre `CreateEditorInstance` Implementierung aufruft.

    Durch `QueryInterface` Aufrufen können Sie das vorhandene Dokumentdatenobjekt `punkDocDataExisting` untersuchen, das im Parameter angegeben ist.

    Die genauen Schnittstellen, die Sie abfragen müssen, hängen jedoch vom Editor ab, der das Dokument öffnet, wie in Schritt 4 beschrieben.

3. Wenn Sie die entsprechenden Schnittstellen für das vorhandene Dokumentdatenobjekt nicht finden, geben Sie einen Fehlercode an den Editor zurück, der angibt, dass das Dokumentdatenobjekt mit dem Editor nicht kompatibel ist.

    In der Ide-Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>von benachrichtigt Sie ein Meldungsfeld, dass das Dokument in einem anderen Editor geöffnet ist, und fragt, ob Sie es schließen möchten.

4. Wenn Sie dieses Dokument schließen, ruft Visual Studio die Editorfactory ein zweites Mal auf. Bei diesem Aufruf `DocDataExisting` ist der Parameter gleich NULL. Ihre Editor Factory-Implementierung kann dann das Dokumentdatenobjekt in Ihrem eigenen Editor öffnen.

   > [!NOTE]
   > Um zu bestimmen, ob Sie mit einem vorhandenen Dokumentdatenobjekt arbeiten können, können Sie auch [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] private Kenntnisse der Schnittstellenimplementierung verwenden, indem Sie einen Zeiger auf die tatsächliche Klasse Ihrer privaten Implementierung umsetzen. Beispielsweise implementieren `IVsPersistFileFormat`alle Standard-Editoren , <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>die von erben. Daher können Sie `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>für aufrufen, und wenn die Klassen-ID für das vorhandene Dokumentdatenobjekt mit der Klassen-ID Ihrer Implementierung übereinstimmt, können Sie mit dem Dokumentdatenobjekt arbeiten.

## <a name="robust-programming"></a>Stabile Programmierung
 Wenn Visual Studio die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Implementierung der Methode aufruft, wird ein Zeiger `punkDocDataExisting` an das vorhandene Dokumentdatenobjekt im Parameter zurückgeführt, sofern vorhanden. Untersuchen Sie das zurückgegebene `punkDocDataExisting` Dokumentdatenobjekt, um festzustellen, ob das Dokumentdatenobjekt für den Editor geeignet ist, wie in Schritt 4 des Verfahrens in diesem Thema beschrieben. Falls dies angebracht ist, sollte Die Editorfactory eine zweite Ansicht für die Daten bereitstellen, wie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)beschrieben. Wenn dies nicht der Fall ist, sollte eine entsprechende Fehlermeldung angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)
- [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)
