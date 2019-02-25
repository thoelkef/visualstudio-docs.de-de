---
title: Signieren von VSIX-Paketen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 952195ab33b9a7e35265f5ecf40a8de3cf958fb3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720587"
---
# <a name="signing-vsix-packages"></a>Signieren von VSIX-Paketen
Assemblys müssen nicht signiert werden, bevor sie in Visual Studio ausführen können, aber es empfiehlt sich, dafür ist.

 Wenn Sie möchten Ihre Erweiterung zur sicheren, und stellen Sie sicher, dass sie nicht manipuliert wurde, können Sie eine digitale Signatur zu VSIX Package hinzufügen. Bei einer VSIX-Datei signiert ist, wird das VSIX-Installationsprogramm eine Meldung gibt an, dass es, sowie weitere Informationen über die Signatur selbst signiert ist angezeigt. Wenn der Inhalt des VSIX-Projekt geändert wurden, und die VSIX-Datei nicht erneut signiert wurde, zeigt das VSIX-Installationsprogramm, dass die Signatur nicht gültig ist. Die Installation nicht beendet wird, aber der Benutzer wird gewarnt.

> [!IMPORTANT]
>  Ab Visual Studio 2015 können werden VSIX-Pakete, die mit etwas anderes als die Verschlüsselung mit SHA256 signiert identifiziert werden, wie eine ungültige Signatur. VSIX-Installation wird nicht blockiert, aber der Benutzer wird gewarnt werden.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Signieren einer VSIX-Datei mit VSIXSignTool
 Es gibt eine SHA256-Verschlüsselung, Signierung von verfügbaren Tools [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) auf nuget.org auf [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Verwenden Sie die VSIXSignTool

1. VSIX zu einem Projekt hinzufügen.

2. Klicken Sie mit der rechten Maustaste auf den Projektknoten im Projektmappen-Explorer auswählen **hinzufügen &#124; NuGet-Pakete verwalten**.  Weitere Informationen zu NuGet und Hinzufügen von NuGet-Pakete, finden Sie unter den [NuGet-Dokumentation](/NuGet) und [-Paket-Manager-UI](/NuGet/Tools/Package-Manager-UI) Themen.

3. Suchen Sie nach VSIXSignTool aus VisualStudioExtensibility, und installieren Sie das NuGet-Paket.

4. Sie können jetzt die VSIXSignTool von Lokale Pakete-Speicherort des Projekts ausführen. Wenden Sie sich an das Tool die Befehlszeilenhilfe für Ihr Szenario signieren (VSIXSignTool.exe /?).

   Zum Beispiel können Sie mit einem Kennwort geschützte Zertifikatdatei signieren:

   VSIXSignTool.exe anmelden/f \<Certfile >/p \<Kennwort > \<VSIXfile >

## <a name="see-also"></a>Siehe auch
- [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
