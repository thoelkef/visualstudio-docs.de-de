---
title: "Best Practices für die Sicherheit in VSPackages | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c7ceb884ad060ea45c0fd204b5611ce284d3d2af
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-security-in-vspackages"></a>Best Practices für die Sicherheit in VSPackages
So installieren Sie die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] auf dem Computer, müssen Sie in einem Kontext mit Administratorrechten ausgeführt werden. Die grundlegende Einheit der Sicherheit und Bereitstellung von einem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anwendung ist die [VSPackages](../../extensibility/internals/vspackages.md). Ein VSPackage muss registriert werden, mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], erfordert ebenfalls die administrative Anmeldeinformationen.  
  
 Administratoren haben vollständigen Berechtigungen zum Schreiben in die Registrierung und das Dateisystem und Code ausführen. Sie benötigen diese Berechtigungen zum Entwickeln, bereitstellen oder ein VSPackage zu installieren.  
  
 Sobald es installiert ist, ist ein VSPackage voll vertrauenswürdig. Aufgrund dieser hohe Berechtigungsebene ein VSPackage zugeordnet ist es möglich, versehentlich ein VSPackage zu installieren, die bösartigen Absichten.  
  
 Benutzer sollten sicherstellen, dass sie VSPackages nur von vertrauenswürdigen Quellen installieren. Unternehmen, die Entwicklung von VSPackages sollte stark benennen und Sie zu signieren, um dem Benutzer zu gewährleisten, Manipulation verhindert werden. Entwicklung von VSPackages Unternehmen sollten ihre externen Abhängigkeiten, wie z. B. Webdienste und Remoteinstallation, zum Auswerten und beheben Sie etwaige Sicherheitsprobleme untersuchen.  
  
 Weitere Informationen finden Sie unter Richtlinien für das Schreiben von sicheren Code für .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Siehe auch  
 [Add-in-Sicherheit](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX-Sicherheit](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)
