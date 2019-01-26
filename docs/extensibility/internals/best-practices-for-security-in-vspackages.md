---
title: Bewährte Methoden für Sicherheit in VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30c234994fae5799bbb44369edadf9d2f3b82d26
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991137"
---
# <a name="best-practices-for-security-in-vspackages"></a>Bewährte Methoden für die Sicherheit in VSPackages
So installieren Sie die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] auf dem Computer, müssen Sie in einem Kontext mit Administratorrechten ausgeführt werden. Die grundlegende Einheit von Sicherheit und Bereitstellung von einem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anwendung ist die [VSPackage](../../extensibility/internals/vspackages.md). Eine VSPackage muss registriert werden, mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], wodurch es auch administrative Anmeldeinformationen erforderlich.  
  
 Administratoren haben vollständige Berechtigungen zum Schreiben in die Registrierung und das Dateisystem und Code ausführen. Sie müssen diese Berechtigungen zu entwickeln, bereitstellen, oder installieren eine VSPackage verfügen.  
  
 Sobald sie installiert ist, ist eine VSPackage voll vertrauenswürdig. Aufgrund dieses hohe Maß an Berechtigungen, die ein VSPackage zugeordnet werden soll ist es möglich, versehentlich eine VSPackage zu installieren, die böswillige Absichten hat.  
  
 Benutzer sollten stellen Sie sicher, dass sie VSPackages nur von vertrauenswürdigen Quellen installieren. Unternehmen entwickeln von VSPackages sollte stark benennen und Sie zu signieren, um dem Benutzer zu gewährleisten, Manipulationen verhindert werden. Entwickeln von VSPackages Unternehmen sollten ihre externen Abhängigkeiten auf, wie z. B. Webdienste und remote-Installation, auswerten und beheben Sie alle eventuell vorhandenen Sicherheitsrisiken untersuchen.  
  
 Weitere Informationen finden Sie unter [für .NET Framework Schreiben von sicherem Code](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).  
  
## <a name="see-also"></a>Siehe auch  
 [Add-in-Sicherheit](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX-Sicherheit](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)