---
title: Automatisierungsunterstützung für options Seiten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709931"
---
# <a name="automation-support-for-options-pages"></a>Automatisierungsunterstützung für options Seiten
VSPackages können benutzerdefinierte Dialogfelder für **Optionen** im **Menü Extras** (Extras**options** Seiten) in bereitstellen, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Sie für das Automatisierungs Modell verfügbar machen können.

## <a name="tools-options-pages"></a>Extras (Menü) Optionen (Seiten)
 Zum Erstellen einer Extras **options** Seite muss ein VSPackage eine Implementierung eines Benutzer Steuer Elements bereitstellen, die über die Implementierung der-Methode des VSPackages an die Umgebung zurückgegeben wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> . (Oder für verwalteten Code die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Methode.)

 Es ist optional, aber es wird dringend empfohlen, den Zugriff auf diese neue Seite über das Automatisierungs Modell zuzulassen. Dies kann über die folgenden Schritte erfolgen:

1. Erweitern Sie das <xref:EnvDTE._DTE.Properties%2A> -Objekt durch die Implementierung eines von IDispatch abgeleiteten Objekts.

2. Gibt eine Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> -Methode (oder für verwalteten Code der <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> -Methode) an das von IDispatch abgeleitete Objekt zurück.

3. Wenn ein <xref:EnvDTE._DTE.Properties%2A> automatisierungsconsumer die-Methode auf einer benutzerdefinierten **options** Seite aufruft, verwendet die Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> -Methode, um die Automatisierungs Implementierung einer benutzerdefinierten **Tools-Options** Seite zu erhalten.

4. Das Automatisierungs Objekt des VSPackage wird dann verwendet, um die <xref:EnvDTE.Property> von zurückgegebenen bereitzustellen <xref:EnvDTE._DTE.Properties%2A> .

   Ein Beispiel für das Implementieren der **options** Seite für benutzerdefinierte Tools finden Sie unter [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Weitere Informationen
- [Verfügbar machen von Projekt Objekten](../../extensibility/internals/exposing-project-objects.md)
