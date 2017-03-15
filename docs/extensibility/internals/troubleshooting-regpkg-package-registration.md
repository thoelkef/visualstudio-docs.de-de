---
title: "Problembehandlung RegPkg-Paket-Registrierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RegPkg"
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Problembehandlung RegPkg-Paket-Registrierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio ist mit der PKGDEF\-Dateien. Dies ermöglicht Erweiterung Bereitstellung ohne die Registrierung zugreifen zu müssen. PKGDEF\-Dateien werden erstellt, mit der [CreatePkgDef\-Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md).  
  
 Registrieren Sie ein Paket mithilfe von RegPkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], müssen Sie die Version der RegPkg, die für Ihr Paket geeignet ist, verwenden.  
  
## RegPkg\-Versionen, die im Zusammenhang mit Paketversionen  
 Es gibt zwei Versionen des RegPkg. Eine Version ist in enthalten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Verwenden Sie diese Version, um Pakete zu registrieren, die erstellt wurden, indem Sie eine der folgenden Assemblys:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Folglich können keine Pakete, die mit der früheren Microsoft.VisualStudio.Shell.dll Assembly erstellt wurden.  
  
 Die frühere Version von RegPkg kann Pakete registrieren, die mithilfe der Microsoft.VisualStudio.Shell.dll\-Assembly erstellt wurden. Es kann jedoch keine Pakete, die mit höheren Versionen der Assembly erstellt registrieren.  
  
## Siehe auch  
 [Freigeben eines Produkts](../../misc/releasing-a-visual-studio-integration-product.md)