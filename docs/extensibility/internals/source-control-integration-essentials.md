---
title: "Source Control Integration Essentials | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quellcode-Verwaltungsanbieter essentials"
  - "Quellcode-Verwaltungsanbieter, Übersicht"
  - "Essentials, Quellcode-Verwaltungsanbieter"
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Source Control Integration Essentials
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Arten von Quellcodeverwaltungsintegration: ein Quellcodeverwaltungs\-Plug\-In, die Grundfunktionen bereitstellt und mit dem Quellcodeverwaltungs\-Plug\-In API erstellt wird \(früher als das MSSCCI API\) und eine Projektmappe, die VSPackage\-basierte Quellcodeverwaltungsintegrations robustere Funktionalität bereitstellt.  
  
## Quellcodeverwaltungs\-Plug\-In  
 Ein Quellcodeverwaltungs\-Plug\-In wird als DLL geschrieben, das das Quellcodeverwaltungs\-Plug\-In API implementiert.  Quellcodeverwaltungsintegrations Registrierungs\- und Funktionalität wird durch die API bereitgestellt.  Dieser Ansatz ist einfacher als die Quellcodeverwaltung ein VSPackage implementieren, und es verwendet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche für die meisten Quellcodeverwaltungsvorgänge.  
  
 Um ein Quellcodeverwaltungs\-Plug\-In mit dem Quellcodeverwaltungs\-Plug\-In API zu implementieren, führen Sie folgende Schritte aus:  
  
1.  Erstellen Sie eine DLL, die die Features implementiert, die in [Source Control\-Plug\-ins](../../extensibility/source-control-plug-ins.md)angegeben werden.  
  
2.  Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge ausführen, wie in [Gewusst wie: Installieren Sie ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)beschrieben.  
  
3.  Erstellen Sie eine Hilfe Benutzeroberfläche und zeigen sie an, wenn Sie dazu aufgefordert werden Quellcodeverwaltungs\-Adapter\-Paket \(die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komponente, die durch die Quellcodeverwaltung Quellcodeverwaltung steckverbindungen behandelt\).  
  
 Weitere Informationen finden Sie unter [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## Quellcodeverwaltung VSPackage  
 Eine Quellcodeverwaltung VSPackage\-Implementierung können Sie einen benutzerdefinierten Ersatz für die Benutzeroberfläche der Quellcodeverwaltung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zu entwickeln.  Dieser Ansatz bietet vollständige Kontrolle über Quellcodeverwaltungsintegration, sondern müssen Sie die Benutzeroberflächenelemente bereitstellen und die Quellcodeverwaltung Schnittstellen zu implementieren, die andernfalls unter dem steckbaren Ansatz zur Verfügung gestellt werden.  
  
 So erstellen Sie eine Quellcodeverwaltung VSPackage implementieren, müssen Sie Folgendes:  
  
1.  Erstellen und registrieren Sie ein VSPackage Quellcodeverwaltung verfügen, wie in [Auswahl und Registrierung](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)beschrieben.  
  
2.  Ersetzen Sie die standardmäßigen über die Benutzeroberfläche der Quellcodeverwaltung benutzerdefinierte Benutzeroberfläche.  Weitere Informationen finden Sie unter [Benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Geben Sie die zu verwendenden Symbole angezeigt, und behandeln Sie **Projektmappen\-Explorer** Symbol Events.  Weitere Informationen finden Sie unter [Symbol\-Steuerelement](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Behandeln Sie Abfragen\-Bearbeitung speichern, und fragen Sie [Bearbeiten der Abfragen speichern](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)gezeigt, wie Ereignisse in Punkt ab oder legt diese fest.  
  
 Weitere Informationen finden Sie unter [Erstellen eines VSPackages Datenquellen\-Steuerelement](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## Siehe auch  
 [Übersicht](../../extensibility/internals/source-control-integration-overview.md)   
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Erstellen eines VSPackages Datenquellen\-Steuerelement](../../extensibility/internals/creating-a-source-control-vspackage.md)