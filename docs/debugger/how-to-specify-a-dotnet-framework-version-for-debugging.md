---
title: Geben Sie eine .NET Framework Version für das Debuggen an. Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1f6107d6396c6228be1d511e81003fbe7faf06c9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732641"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Geben Sie eine ältere .NET Framework Version für dasC#Debuggen F#an (, Visual Basic,).

Der Visual Studio-Debugger unterstützt das Debuggen älterer Versionen des Microsoft .NET Frameworks und der aktuellen Version. Wenn Sie eine Anwendung in Visual Studio starten, kann der Debugger immer die richtige Version des .NET Framework für die Anwendung identifizieren, die Sie Debuggen. Wenn die Anwendung jedoch bereits ausgeführt wird und Sie das Debuggen mithilfe von **Anfügen an**starten, kann der Debugger möglicherweise nicht immer eine ältere Version des .NET Framework identifizieren. Dann erhalten Sie eine Fehlermeldung, die besagt,

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

In den seltenen Fällen, in denen dieser Fehler auftritt, können Sie einen Registrierungsschlüssel festlegen, um den Debugger anzugeben, welche Version verwendet werden soll.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>So geben Sie eine .NET Framework-Version für das Debuggen an

1. Durchsuchen Sie das Verzeichnis Windows\Microsoft.NET\Framework, um zu bestimmen, welche Versionen von .NET Framework auf dem Computer installiert sind. Die Versionsnummern haben folgendes Format:

    `V1.1.4322`

    Identifizieren Sie die richtige Versionsnummer, und notieren Sie sie.

2. Starten Sie den **Registrierungs-Editor** (regedit).

3. Öffnen Sie im **Registrierungs-Editor** den Ordner HKEY_LOCAL_MACHINE.

4. Navigieren Sie zu HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}.

    Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, und klicken Sie auf **Neuer Schlüssel**. Benennen Sie den neuen Schlüssel `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.

5. Suchen Sie unter {449EC4CC-30D2-4032-9256-EE18EB41B62B} in der Spalte **Name** den Schlüssel CLRVersionForDebugging.

   1. Wenn der Schlüssel nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf {449EC4CC-30D2-4032-9256-EE18EB41B62B}, und klicken Sie dann auf **Neuer Zeichenfolgenwert**. Klicken Sie mit der rechten Maustaste auf den neuen Zeichen folgen Wert, klicken Sie auf **Umbenennen**, und geben Sie `CLRVersionForDebugging`

6. Doppelklicken Sie auf **CLRVersionForDebugging**.

7. Geben Sie im Feld **Zeichenfolge bearbeiten** die .NET Framework-Versionsnummer in das Feld **Wert** ein. Beispiel: V1.1.4322

8. Klicken Sie auf **OK**.

9. Schließen Sie den **Registrierungs-Editor**.

     Wenn beim Starten des Debuggens weiterhin eine Fehlermeldung angezeigt wird, stellen Sie sicher, dass Sie in der Registrierung die richtige Versionsnummer eingegeben haben. Vergewissern Sie sich außerdem, dass Sie eine Version des .NET Framework verwenden, die von Visual Studio unterstützt wird. Der Debugger ist mit der aktuellen .NET Framework-Version und älteren Versionen kompatibel. Er ist jedoch möglicherweise nicht mit zukünftigen Versionen kompatibel.

## <a name="see-also"></a>Siehe auch
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)