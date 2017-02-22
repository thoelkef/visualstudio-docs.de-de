---
title: "Benutzeroberfl&#228;chenautomatisierungs-Unterst&#252;tzung f&#252;r Optionen (Seiten) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Optionen (Seiten) Tools [Visual Studio SDK] Benutzeroberflächenautomatisierungs-Unterstützung"
  - "Automatisierung [Visual Studio SDK] Optionsseiten im Menü Extras erstellen"
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Benutzeroberfl&#228;chenautomatisierungs-Unterst&#252;tzung f&#252;r Optionen (Seiten)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackages bieten benutzerdefinierte **Optionen** Dialogfelder die **Tools** Menü \(Optionsseiten im Menü Extras\) in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und können für verfügbar machen das Automatisierungsmodell.  
  
## Tools\-Optionen \(Seiten\)  
 Erstellen einer **Tooloptionen** Seite ein VSPackage Implementierung bereitstellen muss eine Benutzer\-Steuerelement an die Umgebung über das VSPackage\-Implementierung von zurückgegeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> \-Methode \(oder verwaltetem Code die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Methode\).  
  
 Es ist zwar optional, wird jedoch dringend empfohlen, diese neue Seite über das Automatisierungsmodell erlauben. Sie können dies durch die folgenden Schritte ausführen:  
  
1.  Erweitern der <xref:EnvDTE._DTE.Properties%2A> Objekt durch die Implementierung eines Objekts IDispatch abgeleitet.  
  
2.  Eine Implementierung der Zurückgeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode \(oder für verwalteten Code die <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> Methode\) auf die IDispatch abgeleitetes Objekt.  
  
3.  Wenn ein Consumer Automation aufruft die <xref:EnvDTE._DTE.Properties%2A> Methode in einem benutzerdefinierten **Option** auf der Seite die Umgebung verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> \-Methode erhalten eine benutzerdefinierte **Tooloptionen** Seite Automation\-Implementierung.  
  
4.  Das Automatisierungsobjekt des VSPackage wird dann zum jedes <xref:EnvDTE.Property> zurückgegebene <xref:EnvDTE._DTE.Properties%2A>.  
  
 Ein Beispiel eine benutzerdefinierte Tools\-Optionen\-Seite zu implementieren, finden Sie unter [VSSDK\-Beispiele](../../misc/vssdk-samples.md).  
  
## Siehe auch  
 [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)