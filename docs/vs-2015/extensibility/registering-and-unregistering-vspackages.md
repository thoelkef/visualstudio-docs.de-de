---
title: Registrieren und Aufheben der Registrierung von VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193819"
---
# <a name="registering-and-unregistering-vspackages"></a>Registrieren und Aufheben der Registrierung von VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie verwenden Attribute, um ein VSPackage zu registrieren, aber  
  
## <a name="registering-a-vspackage"></a>Registrieren eines VSPackages  
 Mithilfe von Attributen können Sie die Registrierung verwalteter VSPackages steuern. Alle Registrierungsinformationen sind in einer pkgdef-Datei enthalten. Weitere Informationen zur dateibasierten Registrierung finden Sie unter dem [Hilfsprogramm](../extensibility/internals/createpkgdef-utility.md)"|".  
  
 Der folgende Code zeigt, wie Sie das VSPackage mit den standardmäßigen Registrierungs Attributen registrieren.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Aufheben der Registrierung einer Erweiterung  
 Wenn Sie viele verschiedene VSPackages ausprobiert haben und diese aus der experimentellen Instanz entfernen möchten, können Sie einfach den **Reset** -Befehl ausführen. Suchen Sie auf der Startseite des Computers nach **Zurücksetzen der experimentellen Instanz von Visual Studio** , oder führen Sie den folgenden Befehl über die Befehlszeile aus:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Wenn Sie eine Erweiterung deinstallieren möchten, die Sie in Ihrer Entwicklungs Instanz von Visual Studio installiert haben, wechseln Sie zu Extras > **Erweiterungen und Updates**, suchen Sie die Erweiterung, und klicken Sie auf **deinstallieren**.  
  
 Wenn die Erweiterung der Erweiterung aus irgendeinem Grund von keiner dieser Methoden erfolgreich deinstalliert wird, können Sie die Registrierung der VSPackage-Assembly wie folgt von der Befehlszeile aus aufheben:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPackages](../extensibility/internals/vspackages.md)
