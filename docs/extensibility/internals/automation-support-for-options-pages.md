---
title: "-Unterstützung für Optionsseiten | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ffc56e4b36814a8bed7a0f93d66cc87c0b6fc466
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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