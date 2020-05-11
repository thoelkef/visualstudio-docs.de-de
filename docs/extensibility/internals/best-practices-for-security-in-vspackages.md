---
title: Bewährte Methoden für die Sicherheit in VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709910"
---
# <a name="best-practices-for-security-in-vspackages"></a>Bewährte Methoden für die Sicherheit in VSPackages
Um die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] auf Ihrem Computer zu installieren, müssen Sie in einem Kontext mit administrativen Anmeldeinformationen ausgeführt werden. Die grundlegende Einheit für Sicherheit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und Bereitstellung einer Anwendung ist das [VSPackage](../../extensibility/internals/vspackages.md). Ein VSPackage muss mithilfe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]von registriert werden, was auch administrative Anmeldeinformationen erfordert.

 Administratoren verfügen über vollständige Berechtigungen zum Schreiben in die Registrierung und zum Dateisystem sowie zum Ausführen von Code. Sie müssen über diese Berechtigungen verfügen, um ein VSPackage zu entwickeln, bereitzustellen oder zu installieren.

 Sobald es installiert ist, ist ein VSPackage voll vertrauenswürdig. Aufgrund dieser hohen Berechtigungsstufe, die einem VSPackage zugeordnet ist, ist es möglich, versehentlich ein VSPackage mit böswilliger Absicht zu installieren.

 Benutzer sollten sicherstellen, dass sie VSPackages nur aus vertrauenswürdigen Quellen installieren. Unternehmen, die VSPackages entwickeln, sollten sie stark benennen und signieren, um dem Benutzer zu versichern, dass Manipulationen verhindert werden. Unternehmen, die VSPackages entwickeln, sollten ihre externen Abhängigkeiten, wie Webdienste und Remoteinstallation, untersuchen, um Sicherheitsprobleme zu bewerten und zu beheben.

 Weitere Informationen finden Sie unter [Richtlinien für sichere Codierung für .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Weitere Informationen
- [Add-In-Sicherheit](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [DDEX-Sicherheit](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
