---
title: Problembehandlung bei Registrierung des RegPkg-Pakets | Microsoft-Dokumentation
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
ms.openlocfilehash: 5424ca9a1a51088a020d04faa55754ad487d5723
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910536"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Problembehandlung bei der Registrierung des RegPkg-Pakets
> [!NOTE]
>  Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio wird mithilfe der PKGDEF-Dateien. Dadurch für die erweiterungsbereitstellung ohne die Registrierung des Systems zugreifen zu müssen. PKGDEF-Dateien werden erstellt, mit der [CreatePkgDef-Hilfsprogramm](../../extensibility/internals/createpkgdef-utility.md).  
  
 Ein Paket zu registrieren, indem Sie mithilfe von RegPkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], müssen Sie die Version des RegPkg, die für Ihr Paket geeignet ist, verwenden.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg-Versionen, die im Zusammenhang mit der Paketversionen  
 Es gibt zwei Versionen des regpkg entsprechend an. Eine Version befindet sich im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Verwenden Sie diese Version, um Pakete zu registrieren, die mit einer der folgenden Assemblys erstellt wurden:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Es kann keine Pakete registrieren, die mit der früheren Microsoft.VisualStudio.Shell.dll erstellt wurden.  
  
   Die frühere Version des RegPkg kann Pakete registrieren, die mit der Microsoft.VisualStudio.Shell.dll erstellt wurden. Es kann jedoch nicht Pakete, die mit höheren Versionen der Assembly erstellt registrieren.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../../extensibility/internals/vspackages.md)