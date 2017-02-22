---
title: "Automatisierte f&#252;r VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, Automatisierung [Visual Studio SDK]"
  - "Automatisierung [Visual Studio SDK] VSPackages"
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Automatisierte f&#252;r VSPackages
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Es gibt zwei Hauptmethoden zur Automatisierung für Ihre VSPackages: durch die Implementierung von VSPackage\-Objekten und durch die Implementierung von standard\-Automatisierungsobjekte. Im Allgemeinen werden diese zusammen verwendet, das Automatisierungsmodell der Umgebung zu erweitern.  
  
## VSPackage\-Objekten  
 Bestimmte Stellen in der Benutzeroberflächenautomatisierungs\-Modell müssen Sie Automatisierungsobjekte angeben, die um das VSPackage eindeutig sind. Neue Projekte erfordern z. B. verschiedene Objekte, die nur das VSPackage bereitstellt. Die Namen dieser Objekte werden in der Registrierung eingegeben und durch das Aufrufen der Umgebung abgerufen `DTE` Objekt.  
  
 VSPackage\-Objekte können auch abgerufen werden, wenn ein Consumer Automatisierung, das Objekt über den Objekt\-Eigenschaft eines standard\-Objekts bereitgestellt verwendet. Z. B. der Standard `Window` Objekt verfügt über eine `Object` \-Eigenschaft, häufig als bezeichnet die `Windows.Object` Eigenschaft. Bei Consumern der `Window.Object` in einem Fenster in Ihre VSPackage implementiert, übergeben Sie wieder einen bestimmten Automatisierungsobjekt des eigenen Entwurfs.  
  
#### Projekte  
 VSPackages kann das Automatisierungsmodell für die neuen Typen über ihre eigenen VSPackage\-Objekten. Der primäre Zweck der Bereitstellung neuer Automatisierungsobjekte für Ihr VSPackage Projekts eindeutig zu unterscheiden, Objekte aus einer <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> oder ein <xref:VSLangProj80.VSProject2> Objekt. Diese Unterscheidung ist praktisch, wenn bieten die Möglichkeit einzelne oder durchlaufen den Typ des Projekts, abgesehen von anderen Projekttypen sollten diese Seite\-an\-Seite angezeigt werden sollen in einer Projektmappe. Weitere Informationen finden Sie unter [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md).  
  
#### Ereignisse  
 Die Ereignisarchitektur der Umgebung bietet eine andere Stelle für Sie, Ihre eigenen VSPackage\-spezifische Objekte angefügt werden soll. Erstellen Sie eine eigene eindeutige Ereignisobjekte, können Sie z. B. die Umgebung Ereignismodell für Projekte erweitern. Sie möchten möglicherweise Geben Sie Ihre eigenen Ereignisse, wenn Sie Ihren eigenen Projekttyp ein neues Element hinzugefügt wird. Weitere Informationen finden Sie unter [Das Offenlegen von Ereignissen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### Fensterobjekte  
 Windows können ein VSPackage\-spezifische\-Automatisierungsobjekt wieder zurück an die Umgebung, die beim Aufruf übergeben werden. Sie implementieren ein Objekt, das von abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> oder `IDispatch` die Hände wieder Eigenschaften, erweitern das Window\-Objekt, in dem diese platziert. Beispielsweise können Sie diesen Ansatz zur Automatisierung für ein Steuerelement in einem Fensterrahmen positioniert. Die Semantik für dieses Objekt und alle anderen Objekte, die sie erweitern kann können Sie nach Belieben zu entwerfen. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen von Automatisierung für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### Optionsseiten im Menü Extras  
 Sie können Seiten, um die Tools, Optionen Automatisierungsmodell durch Implementieren von Seiten und Hinzufügen von Informationen in der Registrierung erstellen Ihre eigenen Optionen zu erweitern, erstellen. Die Seiten können dann über das Umgebungsobjektmodell wie alle anderen Optionsseiten aufgerufen werden. Wenn der Entwurf der Funktion, die Sie der Umgebung von VSPackages hinzufügen Optionsseiten erfordert, sollten Sie auch die Benutzeroberflächenautomatisierungs\-Unterstützung hinzufügen. Weitere Informationen finden Sie unter [Benutzeroberflächenautomatisierungs\-Unterstützung für Optionen \(Seiten\)](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## Standard\-Automatisierungsobjekte  
 Um die Automatisierung für Projekte zu erweitern, implementieren Sie auch standard\-Automatisierungsobjekte \(abgeleitet von `IDispatch`\), die neben anderen Projektobjekte stehen und standard\-Methoden und Eigenschaften implementieren. Beispiele für standard\-Objekte sind die Projektobjekte, die in der Projektmappenhierarchie, wie z. B. eingefügt werden `Projects`, `Project`, `ProjectItem`, und `ProjectItems`. Alle neuen Projekttyp sollten diese Objekte \(und möglicherweise anderen Einstellungen je nach Semantik des Projekts\) implementieren.  
  
 In gewisser Hinsicht bieten diese Objekte den entgegengesetzten Vorteil der Projekt\-Objekten VSPackage. Die standard\-Automatisierungsobjekte können Ihr Projekt in ein standardisiertes Mittel wie jedes andere Projekt unterstützen die gleichen Objekte verwendet werden. Folglich ein Add\-in, das für allgemeine geschrieben wird `Project` und `ProjectItem` Objekte können für Projekte eines beliebigen Typs fungieren. Weitere Informationen finden Sie unter [Projekt\-Modellierung](../../extensibility/internals/project-modeling.md).