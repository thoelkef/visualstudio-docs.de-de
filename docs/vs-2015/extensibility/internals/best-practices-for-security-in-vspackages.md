---
title: Bewährte Methoden für die Sicherheit in VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697265"
---
# <a name="best-practices-for-security-in-vspackages"></a>Bewährte Methoden für die Sicherheit in VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um das auf dem Computer zu installieren [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , müssen Sie in einem Kontext mit Administrator Anmelde Informationen ausgeführt werden. Die grundlegende Einheit der Sicherheit und Bereitstellung einer- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Anwendung sind die [VSPackages](../../extensibility/internals/vspackages.md). Ein VSPackage muss mithilfe von registriert werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , wofür auch administrative Anmelde Informationen erforderlich sind.  
  
 Administratoren verfügen über vollständige Berechtigungen zum Schreiben in die Registrierung und das Dateisystem sowie zum Ausführen von Code. Sie müssen über diese Berechtigungen verfügen, um ein VSPackage zu entwickeln, bereitzustellen oder zu installieren.  
  
 Sobald Sie installiert ist, wird ein VSPackage als voll vertrauenswürdig eingestuft. Aufgrund dieses hohen Berechtigungs Niveaus, das einem VSPackage zugeordnet ist, ist es möglich, versehentlich ein VSPackage mit böswilliger Absicht zu installieren.  
  
 Benutzer sollten sicherstellen, dass Sie VSPackages nur aus vertrauenswürdigen Quellen installieren. Unternehmen, die VSPackages entwickeln, sollten diese stark benennen und signieren, um dem Benutzer zu gewährleisten, dass Manipulationen verhindert werden. Unternehmen, die VSPackages entwickeln, sollten Ihre externen Abhängigkeiten (z. b. Webdienste und Remote Installation) untersuchen, um Sicherheitsprobleme auszuwerten und zu beheben.  
  
 Weitere Informationen finden Sie unter Richtlinien für sicheres Programmieren für die .NET Framework ( [https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx) ).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Add-in-Sicherheit](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX-Sicherheit](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
