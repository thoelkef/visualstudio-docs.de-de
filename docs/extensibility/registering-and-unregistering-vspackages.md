---
title: "Registrieren und Aufheben der Registrierung von VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Registrierung VSPackages"
  - "Registrieren von VSPackages"
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
caps.handback.revision: 35
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrieren und Aufheben der Registrierung von VSPackages
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Attribute verwenden, um ein VSPackage zu registrieren, aber  
  
## Registrieren ein VSPackage  
 Attribute können Sie um die Registrierung der verwaltete VSPackages zu steuern. Alle Registrierungsinformationen wird in eine PKGDEF\-Datei enthalten. Weitere Informationen zur Registrierung eines dateibasierten finden Sie unter [CreatePkgDef\-Dienstprogramm](../extensibility/internals/createpkgdef-utility.md).  
  
 Der folgende Code zeigt, wie Sie die standard\-Registrierung Attribute verwenden, um das VSPackage zu registrieren.  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## Aufheben der Registrierung einer Erweiterungs  
 Wenn Sie mit vielen verschiedenen VSPackages ausprobiert haben und sie aus der experimentellen Instanz entfernen möchten, können Sie nur Ausführen der **Zurücksetzen** Befehl. Suchen Sie nach **Zurücksetzen der experimentellen Instanz von Visual Studio** auf der Startseite des Computers, oder führen Sie diesen Befehl von der Befehlszeile aus:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Wenn Sie eine Erweiterung, die Sie für Ihre Entwicklungsinstanz von Visual Studio installiert haben, deinstallieren möchten, wechseln Sie zu **Extras \/ Erweiterungen und Updates**, suchen Sie nach der Erweiterung, und klicken Sie auf **Deinstallieren**.  
  
 Ist aus irgendeinem Grund keine dieser Methoden erfolgreich an die Erweiterung deinstallieren, können Sie die VSPackage\-Assembly, über die Befehlszeile wie folgt aufheben:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)