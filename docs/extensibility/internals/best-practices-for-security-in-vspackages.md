---
title: "Empfohlene Vorgehensweisen für Sicherheit in VSPackages | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 770dff4b531bf4a7347cb648ca4c930b28b79bea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-security-in-vspackages"></a>Best Practices für Sicherheit in VSPackages
So installieren Sie die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] auf Ihrem Computer müssen Sie in einem Kontext mit administrativen Anmeldeinformationen ausgeführt werden. Die grundlegende Einheit von Sicherheit und Bereitstellung von einem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anwendung ist die [VSPackages](../../extensibility/internals/vspackages.md). Eine VSPackage muss registriert werden, mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], erfordert auch die administrative Anmeldeinformationen.  
  
 Administratoren haben vollständigen Berechtigungen zum Schreiben in die Registrierung und das Dateisystem und keinen Code ausführen. Sie müssen diese Berechtigungen zu entwickeln, bereitstellen und installieren eine VSPackage verfügen.  
  
 Sobald sie installiert ist, ist eine VSPackage vollständig vertrauenswürdig. Aufgrund dieser hohes Maß an ein VSPackage zugeordnete Berechtigung ist es möglich, versehentlich eine VSPackage zu installieren, der böswilligen Absichten verfügt.  
  
 Benutzer sollten sicherstellen, dass sie VSPackages nur aus vertrauenswürdigen Quellen installieren. Entwickeln von VSPackages Unternehmen sollten stark benennen und Sie zu signieren, um dem Benutzer zu gewährleisten, Manipulation werden verhindert. Entwickeln von VSPackages Unternehmen sollten ihre externen Abhängigkeiten, z. B. Webdienste und Remoteinstallation, zum Auswerten und beheben alle eventuell vorhandenen Sicherheitsrisiken untersuchen.  
  
 Weitere Informationen finden Sie Richtlinien für das Schreiben von sicheren Code für .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Siehe auch  
 [Add-in-Sicherheit](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX-Sicherheit](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)