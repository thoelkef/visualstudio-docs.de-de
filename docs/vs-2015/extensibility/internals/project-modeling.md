---
title: Projekt Modellierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e0edca4a45419a4a4c962ebf62b65e99c4732a12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431373"
---
# <a name="project-modeling"></a>Projektmodellierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der nächste Schritt bei der Bereitstellung der Automatisierung für Ihr Projekt besteht darin, die Standard Projekt Objekte zu implementieren: die-und-Auflistungen <xref:EnvDTE.Projects> `ProjectItems` , das `Project` - <xref:EnvDTE.ProjectItem> Objekt und das-Objekt sowie die übrigen-Objekte, die für Diese Standardobjekte sind in der Datei "Dteinternal. h" definiert. Eine Implementierung der Standardobjekte wird im bscprj-Beispiel bereitgestellt. Diese Klassen können als Modelle verwendet werden, um eigene Standard Projekt Objekte zu erstellen, die gleichzeitig mit Projekt Objekten von anderen Projekttypen nebeneinander stehen.  
  
 Ein Automatisierungs Consumer nimmt an, dass es möglich <xref:EnvDTE.Solution> ist, ("und ()" aufzurufen, `<UniqueProjName>")` wobei "n" <xref:EnvDTE.ProjectItems> `n` eine Indexnummer zum Abrufen eines bestimmten Projekts in der Projekt Mappe ist. Durch die Durchführung dieses Automatisierungs aufrubens <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> wird die Umgebung in der entsprechenden Projekt Hierarchie aufgerufen, VSITEMID_ROOT als Itemid-Parameter übergeben und als vshpropid-Parameter VSHPROPID_ExtObject. `IVsHierarchy::GetProperty` Gibt einen `IDispatch` Zeiger auf das Automatisierungs Objekt zurück, das die von `Project` Ihnen implementierte Kernschnittstelle bereitstellt.  
  
 Im folgenden finden Sie die Syntax von `IVsHierarchy::GetProperty` .  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projekte ermöglichen das Schachteln und Verwenden von Auflistungen zum Erstellen von Gruppen von Projekt Elementen. Die Hierarchie sieht wie folgt aus.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Schachtelung bedeutet, dass ein- <xref:EnvDTE.ProjectItem> Objekt gleichzeitig eine Auflistung sein kann, da eine Auflistung die geschachtelten- <xref:EnvDTE.ProjectItems> `ProjectItems` Objekte enthalten kann. Das grundlegende Projektbeispiel demonstriert diese Schachtelung nicht. Indem Sie das- `Project` Objekt implementieren, nehmen Sie an der Struktur ähnlichen Struktur Teil, die den Entwurf des gesamten Automatisierungs Modells kennzeichnet.  
  
 Die Projektautomatisierung folgt dem Pfad im folgenden Diagramm.  
  
 ![Objekte in Visual Studio-Projekt](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Projektautomatisierung  
  
 Wenn Sie kein-Objekt implementieren `Project` , gibt die Umgebung immer noch ein generisches- `Project` Objekt zurück, das nur den Namen des Projekts enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>
