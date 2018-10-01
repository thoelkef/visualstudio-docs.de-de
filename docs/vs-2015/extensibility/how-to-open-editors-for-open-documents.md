---
title: 'Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44d3ae5a20269e63e074ec32fd0631312c8d695f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523154"
---
# <a name="how-to-open-editors-for-open-documents"></a>Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente](https://docs.microsoft.com/visualstudio/extensibility/how-to-open-editors-for-open-documents).  
  
Bevor ein Dokumentfenster wird ein Projekt geöffnet wird, muss das Projekt zuerst bestimmen, ob die Datei bereits im Dokumentfenster für einen anderen Editor geöffnet ist. Die Datei kann entweder in einem projektspezifischen-Editor zu öffnen oder einem standard-Editor registriert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Öffnen einen projektspezifischen Editor  
 Verwenden Sie das folgende Verfahren, um für eine Datei eine projektspezifische Editor zu öffnen, die bereits geöffnet ist.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Um für eine geöffnete Datei eine projektspezifische Editor zu öffnen.  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>-Methode auf.  
  
     Dieser Aufruf gibt Zeiger des Dokuments Hierarchie Hierarchieelement und Fensterrahmen, zurück, falls zutreffend.  
  
2.  Wenn das Dokument geöffnet ist, muss das Projekt überprüfen, um festzustellen, ob nur ein dokumentdatenobjekt vorhanden ist, oder ob ein dokumentenansichtsobjekt auch vorhanden ist.  
  
    -   Wenn ein dokumentenansichtsobjekt vorhanden ist, und diese Ansicht für eine andere Hierarchie oder das Hierarchieelement ist, verwendet das Projekt den Zeiger auf den Fensterrahmen für der Ansicht zum vorhandene Fenster zu diesem an.  
  
    -   Wenn ein dokumentenansichtsobjekt vorhanden ist und diese Ansicht für die gleiche Hierarchie und Hierarchieelement ist, können das Projekt eine zweite Ansicht öffnen, wenn es an das zugrunde liegende Datenobjekt von Dokument anfügen kann. Andernfalls sollte das Projekt den Zeiger auf den Fensterrahmen für der Ansicht verwenden, auf diesem vorhandene Fenster.  
  
    -   Wenn nur das dokumentendatenobjekt vorhanden ist, sollte das Projekt bestimmen, ob das dokumentendatenobjekt für seine Ansicht verwendet werden können. Wenn das dokumentendatenobjekt kompatibel ist, vollständige die Schritte erläutert [öffnen einen projektspezifischen Editor](../extensibility/how-to-open-project-specific-editors.md).  
  
     Wenn das dokumentendatenobjekt nicht kompatibel ist, sollte ein Fehler, die dem Benutzer angezeigt werden, der angibt, dass die Datei zurzeit verwendet wird. Dieser Fehler sollte nur in vorübergehende Fälle angezeigt werden, wie z. B. wenn eine Datei zur gleichen Zeit kompiliert wird der Benutzer versucht, zum Öffnen der Datei mit einem Editor außer der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kerntext-Editor. Der kerntext-Editor kann der Compiler dokumentendatenobjekt freigeben.  
  
3.  Wenn das Dokument nicht geöffnet ist, da keine dokumentdatenobjekt oder dokumentenansichtsobjekt vorhanden ist, führen Sie die Schritte in [öffnen einen projektspezifischen Editor](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Wenn Sie eine Standard-Editor öffnen  
 Öffnen Sie mithilfe des folgenden Verfahrens können Sie einen standard-Editor für eine Datei zu öffnen, die bereits ist.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Um einen standard-Editor für eine geöffnete Datei zu öffnen.  
  
1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> auf.  
  
     Diese Methode zunächst überprüft, ob das Dokument nicht bereits geöffnet durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Wenn das Dokument bereits geöffnet ist, und klicken Sie dann das Editorfenster Aufkommen ist.  
  
2.  Wenn das Dokument nicht geöffnet ist, führen Sie die Schritte im [wie: Öffnen Sie Standard-Editoren](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sie öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Vorgehensweise: Öffnen von projektspezifischen Editoren](../extensibility/how-to-open-project-specific-editors.md)   
 [Gewusst wie: Öffnen von Standard-Editoren](../extensibility/how-to-open-standard-editors.md)

