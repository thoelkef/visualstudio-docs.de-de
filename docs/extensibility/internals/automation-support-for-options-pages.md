---
title: Automatisierungssupport für Optionsseiten | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709931"
---
# <a name="automation-support-for-options-pages"></a>Automatisierungsunterstützung für Optionsseiten
VSPackages kann benutzerdefinierte **Optionsdialogfelder** für das Menü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Extras** (Seiten**für Tools-Optionen)** bereitstellen und sie dem Automatisierungsmodell zur Verfügung stellen.

## <a name="tools-options-pages"></a>Extras (Menü) Optionen (Seiten)
 Um eine Seite **"Tools-Optionen"** zu erstellen, muss ein VSPackage eine Benutzersteuerungsimplementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> bereitstellen, die über die Implementierung der Methode durch das VSPackage an die Umgebung zurückgegeben wird. (Oder für verwalteten Code <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> die Methode.)

 Es ist optional, aber dringend empfohlen, den Zugriff auf diese neue Seite über das Automatisierungsmodell zu ermöglichen. Sie können dies mit den folgenden Schritten tun:

1. Erweitern <xref:EnvDTE._DTE.Properties%2A> Sie das Objekt durch die Implementierung eines iDispatch-abgeleiteten Objekts.

2. Geben Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Implementierung der Methode <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> (oder für verwalteten Code die Methode) an das von IDispatch abgeleitete Objekt zurück.

3. Wenn ein Automatisierungsbenutzer <xref:EnvDTE._DTE.Properties%2A> die Methode auf einer benutzerdefinierten **Optionseigenschaftsseite** aufruft, verwendet die Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Methode, um die Automatisierungsimplementierung einer benutzerdefinierten Tools **Options-Seite** abzufragen.

4. Das Automatisierungsobjekt des VSPackage wird <xref:EnvDTE.Property> dann <xref:EnvDTE._DTE.Properties%2A>verwendet, um die von zurückgegebenen bereitzustellen.

   Ein Beispiel zum Implementieren einer benutzerdefinierten **Tools-Optionen-Seite** finden Sie unter [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Weitere Informationen
- [Stellen sie Projektobjekte zur Zeit](../../extensibility/internals/exposing-project-objects.md)
