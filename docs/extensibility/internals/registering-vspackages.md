---
title: Registrieren von VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc8082d63376abeab2da0e8fa7b999c12195d4e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006072"
---
# <a name="registering-vspackages"></a>Registrieren von VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] basiert auf der PKGDEF-Dateien, um zu beschreiben, und suchen Sie eine VSPackage. Eine PKGDEF-Datei enthält alle Registrierungsinformationen, die andernfalls in die systemregistrierung hinzugefügt werden. Verwaltete VSPackages registriert sind, indem Sie das Hinzufügen von Attributen zum Quellcode und die [CreatePkgDef-Hilfsprogramm](../../extensibility/internals/createpkgdef-utility.md) auf die resultierende Assembly zum Generieren einer PKGDEF-Datei.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben des VSPackage-Dateispeicherorts für die VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Beschreibt den Pfad zum Laden für VSPackages.  
  
 [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Erläutert, wie eine VSPackage zu registrieren.  
