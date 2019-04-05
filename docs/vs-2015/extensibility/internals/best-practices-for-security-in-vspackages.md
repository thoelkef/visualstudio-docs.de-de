---
title: Bewährte Methoden für Sicherheit in VSPackages | Microsoft-Dokumentation
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
ms.openlocfilehash: 1db578f62e6fe42ba3d74df5870ca727bd884aaf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957694"
---
# <a name="best-practices-for-security-in-vspackages"></a>Bewährte Methoden für die Sicherheit in VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

So installieren Sie die [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] auf dem Computer, müssen Sie in einem Kontext mit Administratorrechten ausgeführt werden. Die grundlegende Einheit von Sicherheit und Bereitstellung von einem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Anwendung ist die [VSPackages](../../extensibility/internals/vspackages.md). Eine VSPackage muss registriert werden, mithilfe von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], wodurch es auch administrative Anmeldeinformationen erforderlich.  
  
 Administratoren haben vollständige Berechtigungen zum Schreiben in die Registrierung und das Dateisystem und Code ausführen. Sie müssen diese Berechtigungen zu entwickeln, bereitstellen, oder installieren eine VSPackage verfügen.  
  
 Sobald sie installiert ist, ist eine VSPackage voll vertrauenswürdig. Aufgrund dieses hohe Maß an Berechtigungen, die ein VSPackage zugeordnet werden soll ist es möglich, versehentlich eine VSPackage zu installieren, die böswillige Absichten hat.  
  
 Benutzer sollten stellen Sie sicher, dass sie VSPackages nur von vertrauenswürdigen Quellen installieren. Unternehmen entwickeln von VSPackages sollte stark benennen und Sie zu signieren, um dem Benutzer zu gewährleisten, Manipulationen verhindert werden. Entwickeln von VSPackages Unternehmen sollten ihre externen Abhängigkeiten auf, wie z. B. Webdienste und remote-Installation, auswerten und beheben Sie alle eventuell vorhandenen Sicherheitsrisiken untersuchen.  
  
 Weitere Informationen finden Sie in Secure Coding Guidelines für .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Siehe auch  
 [Add-in-Sicherheit](http://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX-Sicherheit](http://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
