---
title: "Projekt-Modellierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automatisierung [Visual Studio SDK], implementieren die Project-Objekte"
  - "Projektmodelle, Automatisierung"
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Projekt-Modellierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der nächste Schritt bei der Automatisierung für das Projekt bereitstellt, ist die Standardeinstellung projektobjekte zu implementieren: <xref:EnvDTE.Projects> und die `ProjectItems`\-Auflistungen. `Project` und die <xref:EnvDTE.ProjectItem>\-Objekte. eindeutig, und die übrigen Objekte zur Implementierung.  Diese Standardeinstellung Objekte werden in Dteinternal.h\-Datei definiert.  Eine Implementierung der standardmäßigen Objekte werden im BscPrj\-Beispiel bereitgestellt.  Sie können diese Klassen als Modelle verwenden, um zu erstellen, Standard projektobjekte verfügen, die mit Projektobjekten von anderen Projekttypen parallel kommunizieren.  
  
 Ein Automatisierungsmodell für geht davon aus, um in der Lage zu sein, <xref:EnvDTE.Solution>aufzurufen \(„`<UniqueProjName>")` und <xref:EnvDTE.ProjectItems> \(`n`\), in der n eine Indexnummer für ein bestimmtes Projekt in der Projektmappe abgerufen wird.  Die Umwandlung diese Automatisierung rufen bewirkt, dass die Umgebung, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> in der entsprechenden Projekthierarchie auf und übergibt VSITEMID\_ROOT als ItemID\-Parameter und VSHPROPID\_ExtObject als VSHPROPID\-Parameter.  `IVsHierarchy::GetProperty` gibt einen `IDispatch` Zeiger auf das Automatisierungsobjekt zurück, das die Kernfunktionen `Project`\-Schnittstelle bereitstellen, die implementiert wurden.  
  
 Im Folgenden wird die Syntax von `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projekte und Auflistungen mit Schachtelung bringen, um Gruppen Projektelemente zu erstellen.  Die Hierarchie sieht wie folgt aus.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Das Schachteln bedeutet, dass ein <xref:EnvDTE.ProjectItem>\-Objekt <xref:EnvDTE.ProjectItems>\-Auflistung gleichzeitig sein kann, da eine `ProjectItems`\-Auflistung die geschachtelten Objekte enthalten kann.  Das grundlegende Projekt Beispiel wird dieser nicht Schachtelungsebene.  Mit dem `Project`\-Objekt implementieren, nehmen Sie an der Struktur strukturähnlichen, die den Entwurf des allgemeinen Automatisierungsmodells kennzeichnet.  
  
 Die sich auf die Projektautomatisierung von folgt dem Pfad im folgenden Diagramm.  
  
 ![Objekte in Visual Studio&#45;Projekt](~/extensibility/internals/media/projectobjects.gif "ProjectObjects")  
sich auf die Projektautomatisierung von  
  
 Wenn Sie kein `Project`\-Objekt implementieren, gibt die Umgebung noch ein generisches `Project`\-Objekt zurück, das nur den Namen des Projekts enthält.  
  
## Siehe auch  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>