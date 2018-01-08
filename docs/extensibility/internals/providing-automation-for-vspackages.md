---
title: "Bereitstellen von Automation für VSPackages | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 63912603a888f3d2c45b8b08a7aba93af0694ab8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="providing-automation-for-vspackages"></a>Bereitstellen von Automation für VSPackages
Es gibt zwei Hauptmethoden, um Automatisierung Ihrer VSPackages bereitzustellen: durch die Implementierung des VSPackage-Objekten und durch die Implementierung von Automation standard-Objekte. Im Allgemeinen werden diese zusammen verwendet, um das Automatisierungsmodell der Umgebung zu erweitern.  
  
## <a name="vspackage-specific-objects"></a>VSPackage-Objekten  
 Bestimmten Stellen in das Automatisierungsmodell erfordern Automatisierungsobjekte bereitstellen, die für Ihr VSPackage eindeutig sind. Neue Projekte erfordern z. B. unterschiedliche Objekte, die nur das VSPackage bereitstellt. Die Namen dieser Objekte werden in der Registrierung eingegeben und über Aufrufe von der Umgebung abgerufen `DTE` Objekt.  
  
 VSPackage-Objekten können auch abgerufen werden, wenn ein Consumer Automation das Objekt, das über die Objekteigenschaft eines standard-Objekts bereitgestellt, verwendet. Z. B. der Standard `Window` Objekt verfügt über eine `Object` Eigenschaft, die häufig als bezeichnet den `Windows.Object` Eigenschaft. Bei Consumern der `Window.Object` auf ein Fenster, in das VSPackage implementiert, übergeben Sie wieder eine bestimmte Automatisierungsobjekt selbst entworfenen.  
  
#### <a name="projects"></a>Projekte  
 VSPackages können über das Automatisierungsmodell für neue Projekttypen über ihre eigenen VSPackage-spezifische Objekte erweitern. Der primäre Zweck von Bereitstellen neuer Automatisierungsobjekte für Ihr VSPackage besteht darin, eindeutige Projekt unterscheiden Objekte aus einer <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> oder ein <xref:VSLangProj80.VSProject2> Objekt. Diese Unterscheidung ist praktisch, wenn bieten die Möglichkeit, einzelne oder durchlaufen den Typ des Projekts, abgesehen von anderen Projekttypen weisen sollten diese Seite-an-Seite angezeigt werden sollen in einer Projektmappe. Weitere Informationen finden Sie unter [Projektobjekten Verfügbarmachen von](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Ereignisse  
 Die Ereignisarchitektur der Umgebung bietet eine andere Stelle für Sie, Ihren eigenen VSPackage-Objekte angefügt werden soll. Erstellen Sie Ihre eigenen eindeutigen Ereignisobjekten, können Sie z. B. die Umgebung Ereignismodell für Projekte erweitern. Möglicherweise bieten möchten Ihre eigenen Ereignisse aus, wenn Sie Ihren eigenen Projekttyp ein neues Element hinzugefügt wird. Weitere Informationen finden Sie unter [Ereignisse verfügbar machen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Fensterobjekte  
 Windows können eine VSPackage-spezifische Automatisierungsobjekt wieder zurück in die Umgebung, die beim Aufruf übergeben. Sie implementieren ein Objekt, das von abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> oder `IDispatch` übergibt, die zurück an Eigenschaften, erweitern das Window-Objekt, in dem es positioniert ist. Beispielsweise können Sie diesen Ansatz, um Automatisierung für ein Steuerelement in einen Fensterrahmen positioniert bereitzustellen. Die Semantik dieses Objekts und beliebiger anderer Objekte, die sie möglicherweise erweitert werden Ihnen entwerfen. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen von Automation für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Optionsseiten im Menü "Extras"  
 Sie können Seiten, um die Tools, Optionen Automatisierungsmodell durch das Implementieren von Seiten und Hinzufügen von Informationen zur Registrierung Erstellen eigener Optionen bieten eine Erweiterung erstellen. Die Seiten können dann über das Umgebungsobjektmodell wie alle anderen Optionsseiten aufgerufen werden. Wenn der Entwurf der Funktion, die Sie mit der Umgebung über VSPackages hinzufügen (Seiten) erfordert, sollten Sie die automatisierungsunterstützung hinzufügen. Weitere Informationen finden Sie unter [-Unterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Automation Standard-Objekte  
 Um die Automatisierung für Projekte zu erweitern, implementieren Sie darüber hinaus Automation standard-Objekte (abgeleitet von `IDispatch`), die neben anderen Projektobjekte stehen, und Implementieren von standard-Methoden und Eigenschaften. Beispiele für standard-Objekte sind die Projektobjekte, die in der Projektmappenhierarchie, z. B. eingefügt werden `Projects`, `Project`, `ProjectItem`, und `ProjectItems`. Alle neuen Projekttyp sollten diese Objekte (und möglicherweise auch anderen werden abhängig von der Semantik des Projekts) implementieren.  
  
 Geben Sie in dem Sinn diese Objekte den entgegengesetzten Vorteil, dass die VSPackage-spezifische Projektobjekte. Die standard-Automatisierungsobjekte ermöglichen das Projekt auf eine generalisierte Weise wie alle anderen Projekte unterstützen die gleichen Objekte verwendet werden. Daher ein Add-in, das für allgemeine geschrieben wird `Project` und `ProjectItem` Objekte können für Projekte eines beliebigen Typs fungieren. Weitere Informationen finden Sie unter [Projekt modellieren](../../extensibility/internals/project-modeling.md).