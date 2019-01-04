---
title: 'Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4ba9e15a7f7578454aa7b87372ea776399eca57
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967306"
---
# <a name="how-to-open-editors-for-open-documents"></a>Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente
Bevor ein Dokumentfenster wird ein Projekt geöffnet wird, muss das Projekt zuerst bestimmen, ob die Datei bereits im Dokumentfenster für einen anderen Editor geöffnet ist. Die Datei kann entweder in einem projektspezifischen-Editor zu öffnen oder einem standard-Editor registriert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="open-a-project-specific-editor"></a>Öffnen Sie einen projektspezifischen editor  
 Verwenden Sie das folgende Verfahren, um für eine Datei eine projektspezifische Editor zu öffnen, die bereits geöffnet ist.  
  
### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Um für eine geöffnete Datei eine projektspezifische Editor zu öffnen.  
  
1. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>-Methode auf.  
  
    Dieser Aufruf gibt Zeiger des Dokuments Hierarchie Hierarchieelement und Fensterrahmen, zurück, falls zutreffend.  
  
2. Wenn das Dokument geöffnet ist, muss das Projekt überprüfen, um festzustellen, ob nur ein dokumentdatenobjekt vorhanden ist, oder ob ein dokumentenansichtsobjekt auch vorhanden ist.  
  
   - Wenn ein dokumentenansichtsobjekt vorhanden ist, und diese Ansicht für eine andere Hierarchie oder das Hierarchieelement ist, verwendet das Projekt den Zeiger auf den Fensterrahmen für der Ansicht zum vorhandene Fenster zu diesem an.  
  
   - Wenn ein dokumentenansichtsobjekt vorhanden ist und diese Ansicht für die gleiche Hierarchie und Hierarchieelement ist, können das Projekt eine zweite Ansicht öffnen, wenn es an das zugrunde liegende Datenobjekt von Dokument anfügen kann. Andernfalls sollte das Projekt den Zeiger auf den Fensterrahmen für der Ansicht verwenden, auf diesem vorhandene Fenster.  
  
   - Wenn nur das dokumentendatenobjekt vorhanden ist, sollte das Projekt bestimmen, ob das dokumentendatenobjekt für seine Ansicht verwendet werden können. Wenn das dokumentendatenobjekt kompatibel ist, vollständige die Schritte erläutert [öffnen Sie einen projektspezifischen Editor](../extensibility/how-to-open-project-specific-editors.md).  
  
     Wenn das dokumentendatenobjekt nicht kompatibel ist, sollte ein Fehler, die dem Benutzer angezeigt werden, der angibt, dass die Datei zurzeit verwendet wird. Dieser Fehler sollte nur in vorübergehende Fälle angezeigt werden, wie z. B. wenn eine Datei zur gleichen Zeit kompiliert wird der Benutzer versucht, zum Öffnen der Datei mit einem Editor außer der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kerntext-Editor. Der kerntext-Editor kann der Compiler dokumentendatenobjekt freigeben.  
  
3. Wenn das Dokument nicht geöffnet ist, da keine dokumentdatenobjekt oder dokumentenansichtsobjekt vorhanden ist, führen Sie die Schritte in [öffnen Sie einen projektspezifischen Editor](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="open-a-standard-editor"></a>Öffnen Sie einen standard-editor  
 Öffnen Sie mithilfe des folgenden Verfahrens können Sie einen standard-Editor für eine Datei zu öffnen, die bereits ist.  
  
### <a name="to-open-a-standard-editor-for-an-open-file"></a>Um einen standard-Editor für eine geöffnete Datei zu öffnen.  
  
1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> auf.  
  
     Diese Methode zunächst überprüft, ob das Dokument nicht bereits geöffnet durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Wenn das Dokument bereits geöffnet ist, und klicken Sie dann das Editorfenster Aufkommen ist.  
  
2.  Wenn das Dokument nicht geöffnet ist, führen Sie die Schritte im [Vorgehensweise: Öffnen Sie die standard-Editoren](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Vorgehensweise: Öffnen von projektspezifischen Editoren](../extensibility/how-to-open-project-specific-editors.md)   
 [Vorgehensweise: Open-standard-Editoren](../extensibility/how-to-open-standard-editors.md)
