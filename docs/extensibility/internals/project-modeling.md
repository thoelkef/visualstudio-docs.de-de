---
title: Projektmodellierung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706553"
---
# <a name="project-modeling"></a>Projektmodellierung
Der nächste Schritt bei der Bereitstellung von Automatisierung für <xref:EnvDTE.Projects> Ihr `ProjectItems` Projekt besteht darin, die Standardprojektobjekte zu implementieren: die und Sammlungen; die `Project` <xref:EnvDTE.ProjectItem> und Objekte; und die verbleibenden Objekte, die für Ihre Implementierung eindeutig sind. Diese Standardobjekte sind in der Datei Dteinternal.h definiert. Eine Implementierung der Standardobjekte wird im BscPrj-Beispiel bereitgestellt. Sie können diese Klassen als Modelle verwenden, um eigene Standardprojektobjekte zu erstellen, die Seite an Seite mit Projektobjekten aus anderen Projekttypen stehen.

 Ein Automatisierungsverbraucher geht davon aus,`<UniqueProjName>")` dass <xref:EnvDTE.ProjectItems> `n`er (" und ( ) anrufen <xref:EnvDTE.Solution>kann, wobei n eine Indexnummer zum Abrufen eines bestimmten Projekts in der Projektmappe ist. Wenn Sie diesen Automatisierungsaufruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> tätigen, ruft die Umgebung die entsprechende Projekthierarchie auf, übergibt VSITEMID_ROOT als ItemID-Parameter und VSHPROPID_ExtObject als VSHPROPID-Parameter. `IVsHierarchy::GetProperty`gibt `IDispatch` einen Zeiger auf das Automatisierungsobjekt zurück, das die von Ihnen implementierte Kernschnittstelle `Project` bereitstellt.

 Im Folgenden finden `IVsHierarchy::GetProperty`Sie die Syntax von .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projekte enthalten Verschachtelung und verwenden Auflistungen, um Gruppen von Projektelementen zu erstellen. Die Hierarchie sieht so aus.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Verschachteln bedeutet, dass ein <xref:EnvDTE.ProjectItem> Objekt gleichzeitig aufgenommen werden <xref:EnvDTE.ProjectItems> kann, da eine `ProjectItems` Auflistung die verschachtelten Objekte enthalten kann. Im Beispiel "Basisprojekt" wird diese Verschachtelung nicht veranschaulicht. Durch die `Project` Implementierung des Objekts nehmen Sie an der baumähnlichen Struktur teil, die den Entwurf des gesamten Automatisierungsmodells charakterisiert.

 Die Projektautomatisierung folgt dem Pfad im folgenden Diagramm.

 ![Visual Studio-Projektobjekte](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Projektautomatisierung

 Wenn Sie kein `Project` Objekt implementieren, gibt die `Project` Umgebung weiterhin ein generisches Objekt zurück, das nur den Namen des Projekts enthält.

## <a name="see-also"></a>Weitere Informationen
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
