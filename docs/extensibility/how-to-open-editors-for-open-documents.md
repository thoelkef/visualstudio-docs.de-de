---
title: 'Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 621ed4436160b6f491abb34d8194c75595d9a54c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129805"
---
# <a name="how-to-open-editors-for-open-documents"></a>Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente
Bevor Sie ein Projekt mit einem Dokumentfenster geöffnet wird, muss das Projekt zuerst feststellen, ob die Datei bereits im Dokumentfenster für einen anderen Editor geöffnet ist. Datei kann es sich entweder in einem projektspezifischen-Editor zu öffnen, oder eine der standard-Editoren registriert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Öffnen einen projektspezifische-Editor  
 Verwenden Sie das folgende Verfahren, um eine projektspezifische-Editor für eine Datei zu öffnen, die bereits geöffnet ist.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>So öffnen einen projektspezifische-Editor für eine geöffnete Datei  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>-Methode auf.  
  
     Dieser Aufruf gibt Zeiger an des Dokuments Hierarchie Hierarchieelement und Fensterrahmen, zurück, falls zutreffend.  
  
2.  Wenn das Dokument geöffnet ist, muss das Projekt überprüfen, um festzustellen, ob ein dokumentdatenobjekt vorhanden ist oder wenn ein Dokument Ansichtsobjekt auch vorhanden ist.  
  
    -   Ein Document-Objekt vorhanden ist und in dieser Ansicht wird für eine andere Hierarchie oder Hierarchieelement, verwendet das Projekt den Zeiger auf die Sicht Fensterrahmen zum vorhandene Fenster diesem an.  
  
    -   Ein Document-Objekt vorhanden ist und in dieser Ansicht wird für die gleiche Hierarchie und Hierarchieelement, können das Projekt eine zweite Ansicht öffnen, wenn es an das zugrunde liegende Datenobjekt von Dokument anfügen kann. Verwenden Sie andernfalls sollte das Projekt den Zeiger auf die Sicht Fensterrahmen zum vorhandene Fenster diesem.  
  
    -   Wenn nur das dokumentdatenobjekt vorhanden ist, sollte das Projekt ermitteln, ob das dokumentdatenobjekt für die Ansicht verwendet werden können. Wenn das dokumentdatenobjekt kompatibel ist, vollständige die Schritte im erläutert [öffnen eine projektspezifische-Editors](../extensibility/how-to-open-project-specific-editors.md).  
  
     Wenn das dokumentdatenobjekt nicht kompatibel ist, sollte ein Fehler für den Benutzer angezeigt werden, der angibt, dass die Datei zurzeit verwendet wird. Dieser Fehler sollte nur in vorübergehender Fällen angezeigt werden, z. B. beim Kompilieren einer Datei zur gleichen Zeit der Benutzer versucht, die Datei zu öffnen, mithilfe eines Editors außer der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core Text-Editor. Die Core-Text-Editor kann der Compiler dokumentdatenobjekt freigeben.  
  
3.  Wenn das Dokument nicht geöffnet ist, da keine dokumentdatenobjekt oder dokumentansichtsobjekts vorhanden ist, führen Sie die Schritte in [öffnen eine projektspezifische-Editors](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Öffnen einen Standard-Editor  
 Öffnen Sie mithilfe des folgenden Verfahrens können Sie einen standard-Editor für eine Datei zu öffnen, die bereits ist.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Um eine standard-Editor für eine geöffnete Datei zu öffnen.  
  
1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> auf.  
  
     Diese Methode überprüft zuerst, dass das Dokument nicht bereits geöffnet durch den Aufruf ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Wenn das Dokument bereits geöffnet ist, wird das Editorfenster auftaucht.  
  
2.  Wenn das Dokument nicht geöffnet ist, führen Sie die Schritte im [wie: Öffnen Sie Standard-Editoren](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Vorgehensweise: Öffnen von Editoren projektspezifische](../extensibility/how-to-open-project-specific-editors.md)   
 [Gewusst wie: Öffnen von Standard-Editoren](../extensibility/how-to-open-standard-editors.md)