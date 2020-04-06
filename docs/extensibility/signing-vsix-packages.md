---
title: Signieren von VSIX-Paketen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700087"
---
# <a name="signing-vsix-packages"></a>Signieren von VSIX-Paketen
Erweiterungsassemblys müssen nicht signiert werden, bevor sie in Visual Studio ausgeführt werden können.

 Wenn Sie Ihre Erweiterung sichern und sicherstellen möchten, dass sie nicht manipuliert wurde, können Sie einem VSIX-Paket eine digitale Signatur hinzufügen. Wenn ein VSIX signiert ist, zeigt das VSIX-Installationsprogramm eine Meldung an, die angibt, dass es signiert ist, sowie weitere Informationen zur Signatur selbst. Wenn der Inhalt des VSIX geändert wurde und der VSIX nicht erneut signiert wurde, zeigt das VSIX-Installationsprogramm an, dass die Signatur ungültig ist. Die Installation wird nicht beendet, aber der Benutzer wird gewarnt.

> [!IMPORTANT]
> Ab Visual Studio 2015 werden VSIX-Pakete, die mit einer anderen als SHA256-Verschlüsselung signiert wurden, als ungültige Signatur identifiziert. Die VSIX-Installation wird nicht blockiert, aber der Benutzer wird gewarnt.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Signieren eines VSIX mit VSIXSignTool
 Es ist ein SHA256-Verschlüsselungssignaturtool in [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) auf nuget.org bei [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)verfügbar.

#### <a name="to-use-the-vsixsigntool"></a>So verwenden Sie das VSIXSignTool

1. Fügen Sie Ihr VSIX zu einem Projekt hinzu.

2. Klicken Sie mit der rechten Maustaste auf den Projektknoten im Projektmappen-Explorer, und wählen **Sie Hinzufügen &#124; NuGet-Pakete verwalten**.  Weitere Informationen zu NuGet- und NuGet-Paketen finden Sie in der [NuGet-Dokumentation](/NuGet) und in den Themen [der Paket-Manager-Benutzeroberfläche.](/NuGet/Tools/Package-Manager-UI)

3. Suchen Sie in VisualStudioExtensibility nach VSIXSignTool, und installieren Sie das NuGet-Paket.

4. Sie können das VSIXSignTool jetzt vom Lokalen Paketstandort des Projekts aus ausführen. Konsultieren Sie die Befehlszeilenhilfe des Tools für Ihr Signaturszenario (VSIXSignTool.exe /?).

   Zum Beispiel, um mit einer kennwortgeschützten Zertifikatdatei zu signieren:

   VSIXSignTool.exe Sign \</f certfile \<> \</p Passwort> VSIXfile>

## <a name="see-also"></a>Weitere Informationen
- [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
