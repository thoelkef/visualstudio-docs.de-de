---
title: "Installieren von Visual Studio 2017 | Microsoft-Dokumentation"
description: "Erfahren Sie Schritt für Schritt, wie Sie Visual Studio installieren."
ms.custom: 
ms.date: 05/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 9f7c1d33191adf3fb54cf59cd98ae5fffe14eee4
ms.contentlocale: de-de
ms.lasthandoff: 05/31/2017

---
# <a name="install-visual-studio-2017"></a>Installieren von Visual Studio 2017
Willkommen Sie bei einer neuen Möglichkeit zur Installation von Visual Studio. Mit unserer neuesten Version können Sie nun ganz einfach nur die Funktionen auswählen und installieren, die Sie benötigen. Gleichzeitig wurde der Mindestbedarf an Speicherplatz für Visual Studio reduziert, sodass die Installation schneller erfolgt und mit geringeren Systembeeinträchtigungen verbunden ist, als je zuvor.

Sie möchten mehr zu weiteren Neuerungen wissen? Sehen Sie sich die [Anmerkungen zur Version](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) an. Ausführlichere Informationen zum neuen Design der Installationsumgebung finden Sie in den Blogbeiträgen [Faster and leaner Visual Studio installer (Visual Studio-Installer schneller und schlanker)](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/) sowie [Anatomy of a low-impact Visual Studio installation (Anatomie einer Visual Studio-Installation mit geringen Auswirkungen)](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/).  

Bereit für die Installation? Schauen Sie sich diese schrittweise Vorführung an.

## <a name="check-system-requirements"></a>Prüfen der Systemanforderungen
Prüfen Sie vor der Installation die [Systemanforderungen](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs), um sicherzugehen, dass Ihr Computer für die Installation von Visual Studio 2017 geeignet ist.

## <a name="download-visual-studio"></a>Herunterladen von Visual Studio
Zuerst müssen Sie Visual Studio herunterladen. Klicken Sie dazu auf diese Schaltfläche, dann auf **Speichern** und anschließend auf **Ordner öffnen**.

 > [!div class="button"]
 > [Visual Studio 2017 herunterladen](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="install-the-installer"></a>Installieren des Installationsprogramms  
Wenn Sie Visual Studio 2017 herunterladen, erhalten Sie eine Bootstrapperdatei, die wiederum das neue Lightweight-Installationsprogramm installiert. Dieses neue Installationsprogramm enthält alles, was Sie benötigen, um Ihre Installation anzupassen.  

> [!IMPORTANT]
> Wenn Sie über ein Preview Release von Visual Studio 2017 auf Ihrem Computer verfügen, werden Sie aufgefordert, dieses vor der Installation von Visual Studio 2017 zu entfernen.

1.  Klicken Sie in Ihrem Ordner **Downloads** doppelt auf die Bootstrapperdatei. Ihr Name kann folgendermaßen lauten:

  * **vs_enterprise.exe** für Visual Studio Enterprise
  * **vs_professional.exe** für Visual Studio Professional
  * **vs_community.exe** für Visual Studio Community  <br><br>

  Wenn eine Benachrichtigung der Benutzerkontensteuerung angezeigt wird, klicken Sie auf **Ja**.  

2.  Sie werden gebeten, die Microsoft-[Lizenzbedingungen](https://www.visualstudio.com/license-terms/) und die Microsoft-[Datenschutzbestimmungen](https://go.microsoft.com/fwlink/?LinkID=824704) zu akzeptieren. Klicken Sie auf **Weiter**.  

   ![Lizenzbedingungen und Datenschutzbestimmungen](~/docs/install/media/vs2017-privacy-and-license-terms.PNG "Microsoft-Lizenzbedingungen und Microsoft-Datenschutzbestimmungen")  

Es werden mehrere Statusbildschirme angezeigt, die den Fortschritt der Installation anzeigen. Nach Abschluss der Installation können Sie die gewünschten Featuregruppen (oder Arbeitsauslastungen) auswählen.

## <a name="install-workloads"></a>Installieren von Arbeitsauslastungen  
 Sie können Ihre Installation mithilfe von Arbeitsauslastungen anpassen. Wählen Sie eine oder mehrere der gewünschten Arbeitsauslastungen aus. Jede Arbeitsauslastung enthält die Features, die Sie für die bevorzugte Programmiersprache oder Plattform benötigen.  

 Gehen Sie für zur Installation folgendermaßen vor:  

1.  Suchen Sie die gewünschten Arbeitsauslastungen im Bildschirm **Visual Studio wird installiert**.  

  ![Visual Studio 2017-Setupdialogfeld](~/docs/install/media/vs2017-workloads.PNG "Installieren von Visual Studio 2017")

     Wählen Sie beispielsweise die Arbeitsauslastung für .NET Desktop-Entwicklung aus. Sie wird mit dem standardmäßigen Kern-Editor bereitgestellt, der die grundlegende Codebearbeitung für über 20 Sprachen, die Möglichkeit, Code aus einem beliebigen Ordner heraus zu öffnen und zu bearbeiten, ohne dass ein Projekt erforderlich ist, und die integrierte Quellcodekontrolle unterstützt.  

2.  Nachdem Sie die gewünschten Arbeitsauslastungen ausgewählt haben, klicken Sie auf **Installieren**.  

    Als Nächstes werden Statusbildschirme angezeigt, die über den Fortschritt der Installation von Visual Studio informieren.

3.  Nachdem die neuen Arbeitsauslastungen und Komponenten installiert wurden, klicken Sie auf **Starten**.

## <a name="install-individual-components"></a>Installieren einzelner Komponenten

Wenn Sie Ihre Visual Studio-Installation nicht mit den praktischen Arbeitsauslastungen anpassen möchten, klicken Sie im Visual Studio-Installer auf die Option **Einzelne Komponenten**, wählen Sie die gewünschten Komponenten aus, und folgen Sie den Anweisungen.

  ![Visual Studio 2017: Installieren einzelner Komponenten](~/docs/install/media/vs2017-components.PNG "Installieren einzelner Visual Studio-Komponenten")

## <a name="install-language-packs"></a>Installieren von Language Packs

Zum Installieren von Visual Studio 2017 in einer bestimmten Sprache Ihrer Wahl klicken Sie im Visual Studio-Installationsprogramm auf die Option **Language Packs** und folgen den Eingabeaufforderungen.

  ![Visual Studio 2017 - Installieren von Language Packs](~/docs/install/media/vs2017-languages.PNG "Installieren von Visual Studio-Language Packs")

### <a name="change-the-installer-language"></a>Ändern der Sprache des Installationsprogramms

Standardmäßig versucht das Installationsprogramm bei der ersten Ausführung die Sprache des Betriebssystems zu verwenden. Das Installationsprogramm speichert diese Einstellung. Sie können die Einstellung ändern, indem Sie das Installationsprogramm über die Befehlszeile ausführen. Mit dem Befehl `vs_installer.exe --locale en-US` können Sie z.B. erzwingen, dass das Installationsprogramm auf Englisch ausgeführt wird. Das Installationsprogramm speichert diese Einstellung für zukünftige Ausführungen. Das Installationsprogramm unterstützt die folgenden Sprachtoken: zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES und tr-TR.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn die Installation von Visual Studio fehlschlägt, lesen Sie den Artikel [Problembehandlung bei der Visual Studio 2017-Installation und Upgradefehlern](troubleshooting-installation-issues.md), um Hilfe bei der Problemlösung zu erhalten.

## <a name="see-also"></a>Siehe auch  
* [Ändern von Visual Studio 2017 RC](modify-visual-studio.md)
* [Aktualisieren von Visual Studio 2017](update-visual-studio.md)
* [Deinstallieren von Visual Studio 2017](uninstall-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017](visual-studio-administrator-guide.md)
* [Melden eines Problems mit Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

