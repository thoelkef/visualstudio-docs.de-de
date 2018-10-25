---
title: Automatisierungsunterstützung für Optionsseiten | Microsoft-Dokumentation
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
ms.openlocfilehash: b18f8df30dc9f3385c2c5f154d66c598b423968e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929646"
---
# <a name="automation-support-for-options-pages"></a>Unterstützung der Automatisierung für Optionsseiten
VSPackages bieten benutzerdefinierte **Optionen** Dialogfelder die **Tools** Menü (**Extras/Optionen** Seiten) in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und können sie für die Automatisierung verfügbar Modell.  
  
## <a name="tools-options-pages"></a>Extras (Menü) Optionen (Seiten)  
 Zum Erstellen einer **Extras/Optionen** Seite muss eine VSPackage eine-Implementierung von Benutzersteuerelementen zurückgegeben, in der Umgebung durch die VSPackage Implementierung bereitstellen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Methode. (Bzw. bei verwaltetem Code, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Methode.) 
  
 Es ist optional, jedoch dringend empfohlen, um den Zugriff auf diese neue Seite über das Automatisierungsmodell zu ermöglichen. Mit den folgenden Schritten können Sie tun:  
  
1. Erweitern Sie die <xref:EnvDTE._DTE.Properties%2A> Objekt durch die Implementierung eines IDispatch abgeleiteten Objekts.  
  
2. Eine Implementierung von Zurückgeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode (oder für verwalteten Code die <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> Methode) auf die IDispatch-abgeleitetes Objekt.  
  
3. Wenn ein automatisierungsbenutzer aufruft der <xref:EnvDTE._DTE.Properties%2A> Methode in einem benutzerdefinierten **Option** auf der Seite auf die Umgebung verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode zum Abrufen eines benutzerdefiniertes **Extras/Optionen** Seite Automation -Implementierung.  
  
4. Das Automatisierungsobjekt des VSPackage wird dann verwendet, um jede bereitzustellen <xref:EnvDTE.Property> zurückgegebenes <xref:EnvDTE._DTE.Properties%2A>.  
  
   Ein Beispiel, das Implementieren eines benutzerdefinierten **Extras/Optionen** finden Sie unter [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)