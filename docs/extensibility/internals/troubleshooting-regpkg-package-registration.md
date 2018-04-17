---
title: Problembehandlung bei der Registrierung des RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4857e41888962a92dced87d63fa2b63161ecac55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-regpkg-package-registration"></a>Problembehandlung bei der Registrierung des RegPkg
> [!NOTE]
>  Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio ist mit der PKGDEF-Dateien. Dies ermöglicht Erweiterung Bereitstellung ohne die Registrierung zugreifen. PKGDEF-Dateien werden erstellt, mit der [CreatePkgDef Utility](../../extensibility/internals/createpkgdef-utility.md).  
  
 So registrieren ein Paket mithilfe von RegPkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], müssen Sie die Version des RegPkg, die für Ihr Paket geeignet ist, verwenden.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg-Versionen, die im Zusammenhang mit Paketversionen  
 Es gibt zwei Versionen des RegPkg. Eine Version ist in enthalten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Verwenden Sie diese Version, um Pakete zu registrieren, die erstellt wurden, indem Sie eine der folgenden Assemblys:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Folglich können keine Pakete, die mit früheren Microsoft.VisualStudio.Shell.dll-Assembly erstellt wurden.  
  
 Die frühere Version von RegPkg kann Pakete registrieren, die mithilfe der Microsoft.VisualStudio.Shell.dll-Assembly erstellt wurden. Es kann jedoch Pakete, die mit höheren Versionen der Assembly erstellt nicht registrieren.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../../extensibility/internals/vspackages.md)