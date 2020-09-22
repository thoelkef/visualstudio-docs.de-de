---
title: Problembehandlung bei der regpkg-Paket Registrierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841068"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Problembehandlung bei der Registrierung des RegPkg-Pakets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio besteht darin, pkgdef-Dateien zu verwenden. Dies ermöglicht die Erweiterungs Bereitstellung, ohne auf die Systemregistrierung zugreifen zu müssen. Pkgdef-Dateien werden mit dem [Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md)"|" erstellt.  
  
 Zum Registrieren eines Pakets mithilfe von regpkg in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] müssen Sie die Version von regpkg verwenden, die für das Paket geeignet ist.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Regpkg-Versionen im Zusammenhang mit Paketversionen  
 Es gibt zwei Versionen von regpkg. Eine Version ist in enthalten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Verwenden Sie diese Version zum Registrieren von Paketen, die mit einer der folgenden Assemblys erstellt wurden:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Pakete, die mithilfe der früheren Microsoft.VisualStudio.Shell.dll Assembly erstellt wurden, können nicht registriert werden.  
  
   Mit der früheren Version von regpkg können Pakete registriert werden, die mit der Microsoft.VisualStudio.Shell.dll-Assembly erstellt wurden. Es ist jedoch nicht möglich, Pakete zu registrieren, die mit neueren Versionen dieser Assembly erstellt wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Freigeben eines Produkts](../../misc/releasing-a-visual-studio-integration-product.md)
