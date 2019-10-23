---
title: Projekt Modellierung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725561"
---
# <a name="project-modeling"></a>Projektmodellierung
Der nächste Schritt bei der Bereitstellung der Automatisierung für Ihr Projekt besteht darin, die Standard Projekt Objekte zu implementieren: die <xref:EnvDTE.Projects>-und `ProjectItems` Auflistungen. Das `Project`-Objekt und das <xref:EnvDTE.ProjectItem>-Objekt. und die restlichen Objekte, die für Ihre Implementierung eindeutig sind. Diese Standardobjekte sind in der Datei "Dteinternal. h" definiert. Eine Implementierung der Standardobjekte wird im bscprj-Beispiel bereitgestellt. Diese Klassen können als Modelle verwendet werden, um eigene Standard Projekt Objekte zu erstellen, die gleichzeitig mit Projekt Objekten von anderen Projekttypen nebeneinander stehen.

 Ein automatisierungsconsumer nimmt an, <xref:EnvDTE.Solution> ("`<UniqueProjName>")` und <xref:EnvDTE.ProjectItems> (`n`) aufzurufen, wobei" n "eine Indexnummer zum Abrufen eines bestimmten Projekts in der Lösung ist. Durch diesen Automatisierungs-Befehl ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> in der entsprechenden Projekt Hierarchie auf, wobei VSITEMID_ROOT als Itemid-Parameter und VSHPROPID_ExtObject als vshpropid-Parameter übergeben wird. `IVsHierarchy::GetProperty` gibt einen `IDispatch` Zeiger auf das Automatisierungs Objekt zurück, das die Kern `Project` Schnittstelle bereitstellt, die Sie implementiert haben.

 Im folgenden finden Sie die Syntax von `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`

 `VSHPROPID` `propid`

 `VARIANT` `*pvar`

 `);`

 Projekte ermöglichen das Schachteln und Verwenden von Auflistungen zum Erstellen von Gruppen von Projekt Elementen. Die Hierarchie sieht wie folgt aus.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Schachtelung bedeutet, dass ein <xref:EnvDTE.ProjectItem> Objekt gleichzeitig <xref:EnvDTE.ProjectItems> Auflistung sein kann, da eine `ProjectItems` Auflistung die geschachtelten Objekte enthalten kann. Das grundlegende Projektbeispiel demonstriert diese Schachtelung nicht. Wenn Sie das `Project`-Objekt implementieren, nehmen Sie an der Struktur ähnlichen Struktur Teil, die den Entwurf des gesamten Automatisierungs Modells kennzeichnet.

 Die Projektautomatisierung folgt dem Pfad im folgenden Diagramm.

 ![Visual Studio-Projekt Objekte](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Projektautomatisierung

 Wenn Sie kein `Project` Objekt implementieren, gibt die Umgebung immer noch ein generisches `Project` Objekt zurück, das nur den Namen des Projekts enthält.

## <a name="see-also"></a>Siehe auch
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>