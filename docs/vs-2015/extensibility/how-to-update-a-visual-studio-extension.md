---
title: Aktualisieren einer Erweiterung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d1464cdd2be79cd93a3e98bcf8769e8f4b8b89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842283"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Gewusst wie: Aktualisieren einer Visual Studio-Erweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Visual Studio-Erweiterung auf Ihrem System aktualisieren, indem Sie **Erweiterungen und Updates** verwenden, um die aktualisierte Version zu installieren. Wenn Sie eine aktualisierte Version einer Erweiterung erstellen, können Sie Sie als aktualisiert markieren, indem Sie die Versionsnummer im VSIX-Manifest erhöhen.

 Updates werden installiert, wenn das VSIX-Manifest der eingehenden Erweiterung identisch mit `ID` dem installierten und einer höheren `Version` Nummer ist. Wenn die `Version` Zahl gleich oder niedriger ist, kann das Paket nicht installiert werden. Wenn die `ID` Werte nicht identisch sind, wird das Paket, das noch nicht installiert ist, als separate Erweiterung erkannt.

 Zur Vermeidung von Konflikten während der Entwicklung empfiehlt es sich, frühere Versionen der aktuell ausgeführten Erweiterungen zu deinstallieren und alle anderen potenziell in Konflikt stehenden Erweiterungen zu deinstallieren bzw. zu deaktivieren.

### <a name="to-update-an-extension-on-your-system"></a>So aktualisieren Sie eine Erweiterung auf dem System

1. Klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**.

2. Klicken Sie im linken Bereich auf **Updates**.

3. Klicken Sie im mittleren Bereich auf das Update, das Sie installieren möchten.

     Die Versionsnummer der aktualisierten Erweiterung wird im rechten Bereich sowie andere Informationen angezeigt.

4. Klicken Sie unten im rechten Bereich auf **Aktualisieren**.

### <a name="to-publish-an-update-of-an-extension"></a>So veröffentlichen Sie ein Update einer Erweiterung

1. Öffnen Sie in Visual Studio die Projekt Mappe für die Erweiterung, die Sie aktualisieren möchten. Nehmen Sie die Änderungen vor.

    > [!IMPORTANT]
    > Unsignierte alle Benutzer Erweiterungen werden nicht automatisch aktualisiert. Sie sollten Ihre Erweiterungen immer signieren.

2. Öffnen Sie in **Projektmappen-Explorer**die Datei Source. Extension. manifest.

3. Vergrößern Sie im Manifest-Designer den Wert der Zahl im Feld **Version** .

4. Speichern Sie die Projekt Mappe, und erstellen Sie Sie.

5. Laden Sie die neue vsix-Datei (im Ordner "\bin\debug\" des Projekts) auf die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website hoch.

     Wenn ein Benutzer, der über eine frühere Version der Erweiterung verfügt, **Erweiterungen und Updates**öffnet, wird die neue Version in der **Update** Liste angezeigt, vorausgesetzt, dass das Tool für die automatische Suche nach Updates festgelegt ist.

     Sie können die automatische Suche nach Updates am unteren Rand des Bereichs " **Updates** " aktivieren oder deaktivieren (**Automatische Erkennung verfügbarer Updates aktivieren/deaktivieren**). Dadurch wird die Einstellung " **nach Updates** suchen" unter Extras > Optionen > Umgebung > **Erweiterungen und Updates**geändert.

    > [!NOTE]
    > Von Visual Studio 2015 Update 2 an können Sie (in **Extras / Optionen / Umgebung / Erweiterungen und Updates**) angeben, ob automatische Updates für Erweiterungen pro Benutzer, alle Benutzererweiterungen oder beides (Standardeinstellung) vorgenommen werden sollen.

## <a name="see-also"></a>Weitere Informationen
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md) suchen [und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)
