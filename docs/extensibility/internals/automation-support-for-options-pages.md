---
title: -Unterstützung für Optionsseiten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d27ad706d4203a3573a734a1cd11b19e3c9df6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="automation-support-for-options-pages"></a>-Unterstützung für Optionsseiten
VSPackages, bieten benutzerdefinierte **Optionen** Dialogfelder, um die **Tools** (Optionsseiten (Tools)) im Menü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und können zur Verfügung stellen, das Automatisierungsmodell.  
  
## <a name="tools-options-pages"></a>Optionsseiten (Tools)  
 Zum Erstellen einer **Extras – Optionen** Seite muss eine VSPackage eine-Implementierung von Benutzersteuerelementen zurückgegeben, mit der Umgebung über die VSPackage Implementierung von Bereitstellen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> -Methode (oder verwaltetem Code die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> die Methode).  
  
 Es ist optional, jedoch dringend empfohlen, den Zugriff auf diese neue Seite über das Automatisierungsmodell. Sie erreichen dies durch die folgenden Schritte aus:  
  
1.  Erweitern der <xref:EnvDTE._DTE.Properties%2A> Objekt über die Implementierung eines Objekts IDispatch abgeleitet.  
  
2.  Eine Implementierung der Zurückgeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode (oder für verwalteten Code die <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> Methode) auf das Objekt IDispatch abgeleitet.  
  
3.  Wenn ein Consumer Automation aufruft der <xref:EnvDTE._DTE.Properties%2A> Methode in einer benutzerdefinierten **Option** Eigenschaftenseite, um die Umgebung verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode, um eine benutzerdefinierte abzurufen **Extras – Optionen** Seite Automatisierung -Implementierung.  
  
4.  Das Automatisierungsobjekt des VSPackage wird dann verwendet, um jedes <xref:EnvDTE.Property> zurückgegebenes <xref:EnvDTE._DTE.Properties%2A>.  
  
 Ein Beispiel für eine benutzerdefinierte Seite "Extras – Optionen" zu implementieren, finden Sie unter [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Siehe auch  
 [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)