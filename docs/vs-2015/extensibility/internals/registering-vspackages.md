---
title: Registrieren von VSPackages | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6bbfc837323ddb103405ab289e89322ddb344040
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243567"
---
# <a name="registering-vspackages"></a>Registrieren von VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] basiert auf der PKGDEF-Dateien, um zu beschreiben, und suchen Sie eine VSPackage. Eine PKGDEF-Datei enthält alle Registrierungsinformationen, die andernfalls in die systemregistrierung hinzugefügt werden. Verwaltete VSPackages registriert sind, indem Sie das Hinzufügen von Attributen zum Quellcode und die [CreatePkgDef-Hilfsprogramm](../../extensibility/internals/createpkgdef-utility.md) auf die resultierende Assembly zum Generieren einer PKGDEF-Datei.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben des VSPackage-Dateispeicherorts für die VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Beschreibt den Pfad zum Laden für VSPackages.  
  
 [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Erläutert, wie eine VSPackage zu registrieren.  
  
 [Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Beschreibt, wie ein Manifest für die Registrierung zu erstellen, die verwendet werden kann, um ein verwaltetes VSPackage bereitzustellen.

