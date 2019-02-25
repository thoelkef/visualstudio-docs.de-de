---
title: CreatePkgDef-Hilfsprogramm | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96b0343cd088a8d608cd3503162bf7fa737b79f4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602441"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef utility
Eine DLL-Datei für Visual Studio-Erweiterung als Parameter akzeptiert und erstellt eine *PKGDEF* Datei zur Ergänzung der *DLL* Datei. Die *PKGDEF* -Datei enthält alle Informationen, die in die systemregistrierung andernfalls geschrieben werden sollen, wenn die Erweiterung installiert ist.

> [!NOTE]
>  Erstellen Sie die Projektvorlagen, die automatisch in Visual Studio SDK enthalten sind die meisten *PKGDEF* Dateien als Teil des Buildprozesses. Dieses Dokument richtet sich für diejenigen, die Pakete manuell erstellen, oder konvertieren Sie vorhandene Pakete verwenden möchten *PKGDEF* Bereitstellung.

## <a name="syntax"></a>Syntax

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumente
 **/ out =&lt;FileName&gt;**  erforderlich sind. Legt den Namen der der *PKGDEF* Ausgabedatei &lt;FileName&gt;.

 **/ codebase** Optional. Erzwingt, dass die Registrierung mit dem **Codebasis** Hilfsprogramm.

 **/ Assembly** erzwingt, dass die Registrierung mit dem **Assembly** Hilfsprogramm.

 **&lt;AssemblyPath&gt;**  den Pfad der *DLL* Datei, die von dem Sie generieren möchten die *PKGDEF*.

## <a name="remarks"></a>Hinweise
 Bereitstellung von Erweiterungen mit *PKGDEF* Dateien ersetzt, die Anforderungen der Registrierung von früheren Versionen von Visual Studio.

 Die *PKGDEF* Dateien müssen in einem der folgenden Speicherorte installiert sein:

- *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*

- *%VSInstallDir%\Common7\IDE\Extensions\\*

  Wenn der Installationsordner *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*, die Erweiterung wird von Visual Studio erkannt, aber standardmäßig deaktiviert sein. Der Benutzer kann mit die Erweiterung aktivieren **Erweiterungen und Updates**.

  Wenn der Installationsordner *%vsinstalldir%\Common7\IDE\Extensions\\*, die Erweiterung ist standardmäßig aktiviert.

> [!NOTE]
>  Die **Erweiterungen und Updates** Tool kann nicht verwendet werden, um eine Erweiterung zugreifen, es sei denn, es als Teil eines VSIX-Pakets installiert ist.

## <a name="see-also"></a>Siehe auch
- [CreateExpInstance-Hilfsprogramm](../../extensibility/internals/createexpinstance-utility.md)