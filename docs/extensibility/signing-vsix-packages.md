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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2e97845c7ef17476e18e0068663772341ad8eb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983111"
---
# <a name="signing-vsix-packages"></a>Signieren von VSIX-Paketen
Erweiterungsassemblys müssen nicht signiert werden, bevor Sie in Visual Studio ausgeführt werden können. Dies ist jedoch eine bewährte Vorgehensweise.

 Wenn Sie Ihre Erweiterung sichern und sicherstellen möchten, dass Sie nicht manipuliert wurde, können Sie einem VSIX-Paket eine digitale Signatur hinzufügen. Wenn eine VSIX signiert ist, zeigt das VSIX-Installationsprogramm eine Meldung mit dem Hinweis an, dass Sie signiert ist, sowie weitere Informationen zur Signatur selbst. Wenn die Inhalte der VSIX geändert wurden und die VSIX nicht erneut signiert wurde, zeigt das VSIX-Installationsprogramm an, dass die Signatur ungültig ist. Die Installation wird nicht beendet, aber der Benutzer ist gewarnt.

> [!IMPORTANT]
> Ab Visual Studio 2015 werden VSIX-Pakete, die mit anderen als SHA256 Encryption signiert werden, als ungültige Signatur identifiziert. Die VSIX-Installation wird nicht blockiert, aber der Benutzer wird gewarnt.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Signieren einer VSIX mit vsixsigntool
 Es gibt ein SHA256 Encryption-Signatur Tool, das unter " [visualstudioextensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) " unter "nuget.org" unter [vsixsigntool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)verfügbar ist.

#### <a name="to-use-the-vsixsigntool"></a>So verwenden Sie das vsixsigntool

1. Fügen Sie die VSIX einem Projekt hinzu.

2. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Projekt Knoten, und wählen **Sie &#124; nuget-Pakete verwalten**aus.  Weitere Informationen zu nuget und zum Hinzufügen von nuget-Paketen finden Sie in den Themen zur [nuget-Dokumentation](/NuGet) und zum [Paket-Manager](/NuGet/Tools/Package-Manager-UI) .

3. Suchen Sie nach vsixsigntool aus visualstudioextensibility, und installieren Sie das nuget-Paket.

4. Sie können jetzt das vsixsigntool aus dem lokalen Paket Speicherort des Projekts ausführen. Weitere Informationen zum Signier Szenario finden Sie in der Befehlszeilen Hilfe des Tools (vsixsigntool. exe/?).

   So können Sie beispielsweise mit einer Kenn Wort geschützten Zertifikatsdatei signieren:

   Vsixsigntool. exe Sign/f \<certfile >/p \<password > \<VSIXfile >

## <a name="see-also"></a>Siehe auch
- [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
