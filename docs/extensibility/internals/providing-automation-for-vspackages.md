---
title: Bereitstellen von Automatisierung für VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b72e1493e8ab00f3aa98f3a9bd8e1e1dd30201e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909076"
---
# <a name="providing-automation-for-vspackages"></a>Bereitstellen von Automatisierung für VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es gibt zwei Hauptmethoden zum Bereitstellen von Automatisierung für VSPackages, die Ihre: durch Implementieren der VSPackage-Objekten und Implementieren von Automation standard-Objekten. Diese werden in der Regel zusammen verwendet, zum Erweitern des Automatisierungsmodells der Umgebung.  
  
## <a name="vspackage-specific-objects"></a>VSPackage-Objekten  
 Bestimmte Stellen in das Automatisierungsmodell müssen Sie Automatisierungsobjekte bereit, die für Ihr VSPackage eindeutig sind. Neue Projekte erfordern beispielsweise verschiedene Objekte, die nur das VSPackage bereitstellt. Die Namen dieser Objekte sind in der Registrierung eingegeben haben, sondern durch Aufrufe von der Umgebung `DTE` Objekt.  
  
 VSPackage-Objekten können auch abgerufen werden, wenn ein automatisierungsbenutzer das Objekt, das über den Objekt-Eigenschaft eines standard-Objekts bereitgestellt wird. Z. B. der Standard `Window` Objekt verfügt über eine `Object` Eigenschaft, die häufig als bezeichnet die `Windows.Object` Eigenschaft. Bei Consumern der `Window.Object` in einem Fenster, in das VSPackage implementiert, übergeben Sie wieder ein bestimmtes Automatisierungsobjekt mit Ihrem eigenen Entwurf.  
  
#### <a name="projects"></a>Projekte  
 VSPackages können über das Automatisierungsmodell für neue Projekttypen über ihre eigenen VSPackage-Objekten erweitern. Der primäre Zweck der Bereitstellung von neuen Automatisierungsobjekte für Ihr VSPackage ist, um Ihr Projekt eindeutig zu unterscheiden, Objekte aus einer <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> oder <xref:VSLangProj80.VSProject2> Objekt. Diese Unterscheidung ist nützlich, wenn bieten die Möglichkeit, einzelne oder durchlaufen den Typ des Projekts, abgesehen von anderen Projekttypen sollten diese Seite-an-Seite angezeigt werden sollen in einer Projektmappe. Weitere Informationen finden Sie unter [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Ereignisse  
 Die Ereignisarchitektur der Umgebung bietet eine andere Stelle für Sie, Ihre eigenen VSPackage-spezifisches Objekte angefügt werden soll. Erstellen Sie Ihre eigenen eindeutigen Ereignis-Objekte, können Sie z. B. der Umgebung Ereignismodell für Projekte erweitern. Sie möchten möglicherweise Geben Sie Ihre eigenen Ereignisse aus, wenn Sie Ihren eigenen Projekttyp ein neues Element hinzugefügt wird. Weitere Informationen finden Sie unter [verfügbar zu machen Ereignisse](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Fensterobjekte  
 Windows kann ein VSPackage-spezifisches Automatisierungsobjekt wieder zurück an die Umgebung, die beim Aufruf übergeben. Sie implementieren ein Objekt, das von abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> oder `IDispatch` , die praktische wieder Eigenschaften erweitern das Window-Objekt, in denen es positioniert ist. Beispielsweise können Sie diesen Ansatz verwenden, um Automatisierung für ein Steuerelement, das im Rahmen eines Fenster positioniert. Die Semantik für dieses Objekt und alle anderen Objekte, die sie erweitern kann gehören Ihnen entwerfen. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen von Automatisierung für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Optionsseiten, auf das Menü "Extras"  
 Sie können Seiten, um die Tools, Optionen Automatisierungsmodell durch das Implementieren von Seiten und Hinzufügen von Informationen in der Registrierung erstellen Ihre eigenen Optionen stellen eine Erweiterung erstellen. Ihre Seiten können dann über das Objektmodell der Umgebung wie alle anderen Optionsseiten aufgerufen werden. Wenn der Entwurf des Features, die Sie in der Umgebung durch VSPackages hinzufügen Optionsseiten erfordert, sollten Sie auch die automatisierungsunterstützung hinzufügen. Weitere Informationen finden Sie unter [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Automation Standard-Objekte  
 Um die Automatisierung für Projekte zu erweitern, implementieren Sie auch Automation standard-Objekte (abgeleitet von `IDispatch`), die neben den anderen Projektobjekten erstellen und implementieren Sie standard-Methoden und Eigenschaften. Beispiele für standard-Objekte sind die Projektobjekte, die in der Projektmappenhierarchie, z. B. eingefügt werden `Projects`, `Project`, `ProjectItem`, und `ProjectItems`. Alle neuen Projekttyp sollten diese Objekte (und möglicherweise andere Lösungen je nach Semantik des Projekts) implementieren.  
  
 In gewisser Hinsicht stellen diese Objekte den entgegengesetzten Vorteil der VSPackage-spezifisches Projektobjekte. Die Automation standard-Objekte können Ihr Projekt in eine generalisierte Methode, wie jedes andere Projekt unterstützen die gleichen Objekte verwendet werden. Daher ein Add-in, die für allgemeine geschrieben werden `Project` und `ProjectItem` Objekte können für Projekte eines beliebigen Typs fungieren. Weitere Informationen finden Sie unter [Projekt Modellierung](../../extensibility/internals/project-modeling.md).
