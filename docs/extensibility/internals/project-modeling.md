---
title: Projekt Modellierung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adb0204afd889ab487070578d136aea736bb63a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="project-modeling"></a>Projekt Modellierung
Der nächste Schritt bei der Bereitstellung von Automation für Ihr Projekt besteht darin, die standard-Projekt-Objekte implementieren: die <xref:EnvDTE.Projects> und `ProjectItems` Sammlungen; das `Project` und <xref:EnvDTE.ProjectItem> Objekte und die übrigen Objekte, die für Ihre Implementierung eindeutig. Diese standard-Objekte werden in Dteinternal.h-Datei definiert. Im Beispiel für den BscPrj wird eine Implementierung der standardmäßigen Objekte bereitgestellt. Sie können diese Klassen als Modelle eigene Objekte standard-Projekt erstellen, die Seite-an-Seite des eigenständigen Bandlaufwerks mit Projektobjekte von anderen Projekttypen.  
  
 Ein Consumer Automatisierung setzt voraus, um aufrufen zu können <xref:EnvDTE.Solution>("`<UniqueProjName>")` und <xref:EnvDTE.ProjectItems> (`n`) wobei n eine Indexnummer zum Abrufen eines bestimmten Projekts in der Projektmappe ist. Diese Automatisierung Aufruf bewirkt, dass die Umgebung Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> auf der entsprechenden Projekthierarchie VSITEMID_ROOT als Element-ID-Parameter und VSHPROPID_ExtObject als: VSHPROPID Parameter übergeben. `IVsHierarchy::GetProperty` Gibt eine `IDispatch` Zeiger auf die Bereitstellung des Kern Automatisierungsobjekt `Project` -Schnittstelle, die Sie implementiert haben.  
  
 Im folgenden ist die Syntax des `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projekte Schachtelung aufzunehmen und Sammlungen verwenden, um Gruppen von Projektelementen zu erstellen. Die Hierarchie sieht wie folgt.  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Schachteln bedeutet, dass eine <xref:EnvDTE.ProjectItem> Objekt kann es sich <xref:EnvDTE.ProjectItems> Auflistung gleichzeitig da eine `ProjectItems` Auflistung kann die geschachtelten Objekte enthalten. Die grundlegende projektbeispiel wird diese Schachtelung nicht veranschaulicht. Durch die Implementierung der `Project` -Objekts können Sie die baumähnlichen-Struktur, die das Design der gesamten Automatisierungsmodell charakterisiert teilnehmen.  
  
 Die Projekt-Automatisierung folgt dem Pfad in der folgenden Abbildung.  
  
 ![Visual Studio-Projektobjekte](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Projekt-Automatisierung  
  
 Wenn Sie nicht implementieren eine `Project` -Objekt die Umgebung wird immer noch eine generische wiederherzustellen `Project` -Objekt, das nur den Namen des Projekts enthält.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>