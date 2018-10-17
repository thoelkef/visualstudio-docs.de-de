---
title: Registrieren und Aufheben der Registrierung von VSPackages | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5f43dd44dde41de4ecf3e34fa5e895ee0f4711f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187615"
---
# <a name="registering-and-unregistering-vspackages"></a>Registrieren und Aufheben der Registrierung von VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie Attribute, zum Registrieren von einer VSPackages, aber  
  
## <a name="registering-a-vspackage"></a>Registriert eine VSPackage  
 Sie können Attribute verwenden, um die Registrierung der verwaltete VSPackages zu steuern. Alle Registrierungsinformationen ist in eine PKGDEF-Datei enthalten. Weitere Informationen zu Datei-basierte Registrierungsschlüssel, finden Sie unter [CreatePkgDef-Hilfsprogramm](../extensibility/internals/createpkgdef-utility.md).  
  
 Der folgende Code zeigt, wie Sie die Registrierungsattribute für die standard-verwenden, um Ihr VSPackage zu registrieren.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Aufheben der Registrierung einer Erweiterungs  
 Wenn Sie mit einer Vielzahl von anderen VSPackages ausprobiert haben und sie aus der experimentellen Instanz entfernen möchten, können Sie nur Ausführen der **zurücksetzen** Befehl. Suchen Sie nach **Zurücksetzen der experimentellen Visual Studio-Instanz** auf der Startseite des Computers, oder führen Sie diesen Befehl über die Befehlszeile:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Wenn Sie möchten eine Erweiterung zu deinstallieren, die Sie für Ihre Entwicklungsinstanz von Visual Studio installiert haben, fahren Sie mit **Extras / Erweiterungen und Updates**, suchen Sie nach der Erweiterung, und klicken Sie auf **Deinstallieren**.  
  
 Wenn aus irgendeinem Grund keine dieser Methoden erfolgreich ist die Erweiterung deinstallieren, können Sie die Registrierung die VSPackage-Assembly, über die Befehlszeile wie folgt aufheben:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)

