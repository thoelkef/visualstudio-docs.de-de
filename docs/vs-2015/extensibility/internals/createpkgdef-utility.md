---
title: Dienstprogramm "|" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840866"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef-Hilfsprogramm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nimmt eine DLL-Datei für eine Visual Studio-Erweiterung als Parameter an und erstellt eine pkgdef-Datei für die DLL-Datei. Die pkgdef-Datei enthält alle Informationen, die andernfalls bei der Installation der Erweiterung in die Systemregistrierung geschrieben werden.  
  
> [!NOTE]
> Die meisten Projektvorlagen, die im Visual Studio SDK enthalten sind, erstellen automatisch pkgdef-Dateien als Teil des Buildprozesses. Dieses Dokument richtet sich an Benutzer, die Pakete manuell erstellen möchten, oder Konvertieren vorhandener Pakete, um die pkgdef-Bereitstellung zu verwenden.  
  
## <a name="syntax"></a>Syntax  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumente  
 /Out =`FileName`  
 Erforderlich. Legt den Namen der pkgdef-Ausgabedatei auf fest `FileName` .  
  
 /codebase  
 (Optional) Erzwingt die Registrierung mit dem CodeBase-Hilfsprogramm.  
  
 /Assembly  
 Erzwingt die Registrierung mit dem Assemblydienstprogramm.  
  
 `AssemblyPath`  
 Der Pfad der DLL-Datei, aus der die pkgdef-Datei generiert werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Erweiterungs Bereitstellung mithilfe von pkgdef-Dateien ersetzt die Registrierungsanforderungen früherer Versionen von Visual Studio.  
  
 Die pkgdef-Dateien müssen an einem der folgenden Speicherorte installiert sein:%localappdata%\microsoft\visual studio\14.0\extensions\ oder%VSInstallDir%\common7\ide\Extensions \\ . Wenn der Installationsordner%LocalAppData%\microsoft\visual studio\14.0\Extensions ist \\ , wird die Erweiterung von Visual Studio erkannt, aber standardmäßig deaktiviert. Der Benutzer kann die Erweiterung mithilfe von **Erweiterungen und Updates**aktivieren. Wenn der Installationsordner%VSInstallDir%\common7\ide\Extensions lautet \\ , ist die Erweiterung standardmäßig aktiviert.  
  
> [!NOTE]
> Das Tool " **Erweiterungen und Updates** " kann nur verwendet werden, um auf eine Erweiterung zuzugreifen, wenn Sie als Teil eines VSIX-Pakets installiert ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CreateExpInstance-Hilfsprogramm](../../extensibility/internals/createexpinstance-utility.md)
