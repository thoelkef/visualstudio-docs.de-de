---
title: Automatisierungsunterstützung für Optionsseiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f7a9a9cf13a50cf13817b4c3b12bd1da1e8370b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512174"
---
# <a name="automation-support-for-options-pages"></a>Automatisierungsunterstützung für Optionsseiten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Automatisierungsunterstützung für Optionsseiten](https://docs.microsoft.com/visualstudio/extensibility/internals/automation-support-for-options-pages).  
  
VSPackages, bieten benutzerdefinierte **Optionen** Dialogfelder die **Tools** (Seiten "Extras/Optionen") im Menü [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und können sie das Automatisierungsmodell zur Verfügung.  
  
## <a name="tools-options-pages"></a>Optionsseiten (Tools)  
 Zum Erstellen einer **Extras/Optionen** Seite muss eine VSPackage eine-Implementierung von Benutzersteuerelementen zurückgegeben, in der Umgebung durch die VSPackage Implementierung bereitstellen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> -Methode (oder verwaltetem Code die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (Methode).  
  
 Es ist optional, jedoch dringend empfohlen, um den Zugriff auf diese neue Seite über das Automatisierungsmodell zu ermöglichen. Sie erreichen dies über die folgenden Schritte aus:  
  
1.  Erweitern Sie die <xref:EnvDTE._DTE.Properties%2A> Objekt durch die Implementierung eines IDispatch abgeleiteten Objekts.  
  
2.  Eine Implementierung von Zurückgeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode (oder für verwalteten Code die <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> Methode) auf die IDispatch-abgeleitetes Objekt.  
  
3.  Wenn ein automatisierungsbenutzer aufruft der <xref:EnvDTE._DTE.Properties%2A> Methode in einem benutzerdefinierten **Option** auf der Seite auf die Umgebung verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode zum Abrufen eines benutzerdefiniertes **Extras/Optionen** Seite Automation -Implementierung.  
  
4.  Das Automatisierungsobjekt des VSPackage wird dann verwendet, um jede bereitzustellen <xref:EnvDTE.Property> zurückgegebenes <xref:EnvDTE._DTE.Properties%2A>.  
  
 Ein Beispiel eine benutzerdefinierte Tools-Optionen-Seite zu implementieren, finden Sie unter [VSSDK-Beispiele](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verfügbarmachen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)

