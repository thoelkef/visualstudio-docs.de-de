---
title: Bewährte Methoden für die Sicherheit in VSPackages | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709910"
---
# <a name="best-practices-for-security-in-vspackages"></a>Bewährte Methoden für die Sicherheit in VSPackages
Um das auf dem Computer zu installieren [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , müssen Sie in einem Kontext mit Administrator Anmelde Informationen ausgeführt werden. Die grundlegende Einheit der Sicherheit und Bereitstellung einer- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anwendung ist das [VSPackage](../../extensibility/internals/vspackages.md). Ein VSPackage muss mithilfe von registriert werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , wofür auch administrative Anmelde Informationen erforderlich sind.

 Administratoren verfügen über vollständige Berechtigungen zum Schreiben in die Registrierung und das Dateisystem sowie zum Ausführen von Code. Sie müssen über diese Berechtigungen verfügen, um ein VSPackage zu entwickeln, bereitzustellen oder zu installieren.

 Sobald Sie installiert ist, wird ein VSPackage als voll vertrauenswürdig eingestuft. Aufgrund dieses hohen Berechtigungs Niveaus, das einem VSPackage zugeordnet ist, ist es möglich, versehentlich ein VSPackage mit böswilliger Absicht zu installieren.

 Benutzer sollten sicherstellen, dass Sie VSPackages nur aus vertrauenswürdigen Quellen installieren. Unternehmen, die VSPackages entwickeln, sollten diese stark benennen und signieren, um dem Benutzer zu gewährleisten, dass Manipulationen verhindert werden. Unternehmen, die VSPackages entwickeln, sollten Ihre externen Abhängigkeiten (z. b. Webdienste und Remote Installation) untersuchen, um Sicherheitsprobleme auszuwerten und zu beheben.

 Weitere Informationen finden Sie unter [Richtlinien für sicheres Programmieren für die .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Weitere Informationen
- [Add-in-Sicherheit](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [DDEX-Sicherheit](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
