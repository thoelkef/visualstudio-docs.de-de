---
title: Projekt Modellierung | Microsoft-Dokumentation
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
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37b237a462900735ea641407d10719d43334262e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808413"
---
# <a name="project-modeling"></a>Projektmodellierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der nächste Schritt im Bereitstellen von Automatisierung für Ihr Projekt ist, um die standard-Projekt-Objekte zu implementieren: die <xref:EnvDTE.Projects> und `ProjectItems` Auflistungen; die `Project` und <xref:EnvDTE.ProjectItem> Objekte und die übrigen Objekte, die für Ihre Implementierung eindeutig. Diese standard-Objekte werden in Dteinternal.h-Datei definiert. Eine Implementierung der standardmäßigen Objekte wird im Beispiel BscPrj bereitgestellt. Sie können diese Klassen als Modelle verwenden, um Ihre eigenen Objekte für die standard-Projekt zu erstellen, die Seite-an-Seite zu stehen mit Projektobjekten aus anderen Projekttypen.  
  
 Setzt voraus, dass ein automatisierungsbenutzer aufrufen können <xref:EnvDTE.Solution>("`<UniqueProjName>")` und <xref:EnvDTE.ProjectItems> (`n`), wobei n ist eine Indexnummer für ein bestimmtes Projekt in der Lösung abrufen. Dieses Automation-Aufruf führt dazu, dass die Umgebung Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> auf den entsprechenden Projekthierarchie übergeben VSITEMID_ROOT als Element-ID-Parameter und VSHPROPID_ExtObject: VSHPROPID-Parameter. `IVsHierarchy::GetProperty` Gibt eine `IDispatch` Zeiger auf die Bereitstellung der Hauptfunktionen der Automatisierungsobjekt `Project` -Schnittstelle, die Sie implementiert haben.  
  
 Im folgenden finden Sie die Syntax der `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projekte Schachtelung aufzunehmen, und Verwenden von Sammlungen zum Erstellen von Gruppen von Projektelementen. Die Hierarchie sieht wie folgt aus.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Schachteln bedeutet, dass eine <xref:EnvDTE.ProjectItem> Objekt kann es sich <xref:EnvDTE.ProjectItems> Auflistung gleichzeitig da eine `ProjectItems` Sammlung kann die geschachtelten Objekte enthalten. Im Beispiel Basic-Projekts wird diese Schachtelung nicht veranschaulicht. Durch die Implementierung der `Project` -Objekts können Sie teilnehmen, in der Baumstruktur, das den Entwurf des allgemeinen Automatisierungsmodells bestimmt.  
  
 Die Projekt-Automatisierung folgt den Pfad in der folgenden Abbildung.  
  
 ![Visual Studio-Projekt-Objekte](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Projekt-Automatisierung  
  
 Wenn Sie nicht implementieren eine `Project` Objekt ist, wird die Umgebung weiterhin einen generischen zurück `Project` -Objekt, das nur den Namen des Projekts enthält.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>

