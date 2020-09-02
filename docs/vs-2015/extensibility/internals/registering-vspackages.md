---
title: Registrieren von VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157391"
---
# <a name="registering-vspackages"></a>Registrieren von VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] stützt sich auf pkgdef-Dateien, um ein VSPackage zu beschreiben und zu suchen. Eine pkgdef-Datei enthält alle Registrierungsinformationen, die andernfalls der Systemregistrierung hinzugefügt würden. Verwaltete VSPackages werden durch Hinzufügen von Attributen zum Quellcode und anschließendem Ausführen des [Dienstprogramms "| atepkgdef](../../extensibility/internals/createpkgdef-utility.md) " für die resultierende Assembly registriert, um eine pkgdef-Datei zu generieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben des VSPackage-Dateispeicherorts für die VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Beschreibt den Lade Pfad für VSPackages.  
  
 [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Erläutert, wie ein VSPackage registriert wird.  
  
 [Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Beschreibt das Erstellen eines Registrierungs Manifests, das zum Bereitstellen eines verwalteten VSPackages verwendet werden kann.
