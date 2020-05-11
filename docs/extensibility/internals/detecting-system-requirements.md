---
title: Erkennen von Systemanforderungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708738"
---
# <a name="detect-system-requirements"></a>Systemanforderungen erkennen
Ein VSPackage kann nur funktionieren, wenn Visual Studio installiert ist. Wenn Sie Microsoft Windows Installer zum Verwalten der Installation Ihres VSPackage verwenden, können Sie das Installationsprogramm so konfigurieren, dass erkannt wird, ob Visual Studio installiert ist. Sie können es auch so konfigurieren, dass das System auf andere Anforderungen überprüft wird, z. B. eine bestimmte Windows-Version oder eine bestimmte Menge an RAM.

## <a name="detect-visual-studio-editions"></a>Visual Studio-Editionen erkennen
 Um festzustellen, ob eine Edition von Visual Studio installiert ist, *(REG_DWORD) 1* stellen Sie sicher, dass sich der Wert des Registrierungsschlüssels **"REG_DWORD)** im entsprechenden Ordner befindet, wie in der folgenden Tabelle aufgeführt. Beachten Sie, dass es eine Hierarchie von Visual Studio-Editionen gibt:

1. Enterprise

2. Professionell

3. Community

Wenn eine neuere Edition installiert wird, werden die Registrierungsschlüssel für diese Edition sowie für frühere Editionen hinzugefügt. Das heißt, wenn die Enterprise-Edition installiert ist, wird der **Installationsschlüssel** auf *1* für Enterprise sowie für die Professional- und Community-Editionen festgelegt. Daher müssen Sie nur nach der neuesten Ausgabe suchen, die Sie benötigen.

> [!NOTE]
> In der 64-Bit-Version des Registrierungseditors werden 32-Bit-Schlüssel unter **HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432Node\\**angezeigt. Die Visual Studio-Schlüssel befinden sich unter **HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432-Knoten-Microsoft-DevDiv-Vs-Servicing\\**.

|Produkt|Schlüssel|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDiv-Vs-Service-Unternehmen|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDiv-Vs-Wartung, 14,0,0,0,0,0,-Professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDiv-Vs-Service-Community|
|Visual Studio 2015 Shell (integriert und isoliert)|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDiv-Vs-Wartung, 14,0, Isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Erkennen, wann Visual Studio ausgeführt wird
 Ihr VSPackage kann nicht ordnungsgemäß registriert werden, wenn Visual Studio ausgeführt wird, wenn das VSPackage installiert ist. Das Installationsprogramm muss erkennen, wann Visual Studio ausgeführt wird, und dann die Installation des Programms verweigern. Windows Installer lässt sie keine Tabelleneinträge verwenden, um eine solche Erkennung zu aktivieren. Stattdessen müssen Sie wie folgt eine benutzerdefinierte `EnumProcesses` Aktion erstellen: Verwenden Sie die Funktion, um den *devenv.exe-Prozess* zu erkennen, und legen Sie dann entweder eine Installer-Eigenschaft fest, die in einer Startbedingung verwendet wird, oder zeigen Sie bedingt ein Dialogfeld an, in dem der Benutzer aufgefordert wird, Visual Studio zu schließen.

## <a name="see-also"></a>Weitere Informationen
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
