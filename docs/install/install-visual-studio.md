---
title: "Installieren von Visual Studio 2017 | Microsoft-Dokumentation"
description: "Erfahren Sie Schritt für Schritt, wie Sie Visual Studio installieren."
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9b37b998347618ea346c3d4e7993d5192c1c82a8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="install-visual-studio-2017"></a>Installieren von Visual Studio 2017
Willkommen Sie bei einer neuen Möglichkeit zur Installation von Visual Studio. In unserer neuesten Version ist es noch einfacher, genau die Features auszuwählen und zu installieren, die Sie benötigen. Wir haben außerdem den mindestens benötigten Speicherplatz weiter verringert, sodass Visual Studio sich schneller und mit geringeren Systemauswirkungen als je zuvor installieren lässt.

Sie möchten mehr zu weiteren Neuerungen in dieser Version wissen? Sehen Sie sich die [Anmerkungen zur Version](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) an.

Bereit für die Installation? Schauen Sie sich diese schrittweise Vorführung an.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Schritt 1: Stellen Sie sicher, dass Ihr Computer für Visual Studio bereit ist

Vor der Installation von Visual Studio:

1. Informieren Sie sich über die [Systemanforderungen](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). Anhand dieser Anforderungen können Sie feststellen, ob Ihr Computer Visual Studio 2017 unterstützt.
2. Laden Sie die aktuellen Windows-Updates herunter. So stellen Sie sicher, dass Ihr Computer sowohl die neuesten Sicherheitsupdates als auch die erforderlichen Systemkomponenten für Visual Studio hat.
3. Starten Sie den Computer neu. Dadurch wird sichergestellt, dass keine ausstehenden Installationen oder Updates die Installation von Visual Studio behindern.
4. Geben Sie Speicherplatz frei. Entfernen Sie nicht benötigte Dateien und Anwendungen z.B. mit der Datenträgerbereinigung-App von Ihrem %Systemlaufwerk%.

Wenn Sie Fragen zum parallelen Ausführen früherer Versionen von Visual Studio mit Visual Studio 2017 haben, lesen Sie den Abschnitt [Kompatibilität mit vorherigen Versionen](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Schritt 2: Herunterladen von Visual Studio

Laden Sie danach die Visual Studio-Bootstrapperdatei herunter. Klicken Sie zu diesem Zweck auf die folgende Schaltfläche, wählen Sie die gewünschte Edition von Visual Studio 2017 aus, und klicken Sie auf **Speichern** und dann auf **Ordner öffnen**.

 > [!div class="button"]
 > [Visual Studio 2017 herunterladen](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
<br/>

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](media/video-icon.png "Video ansehen")  |    [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171), das erläutert, wie Sie die Visual Studio-Bootstrapperdatei herunterladen und die Edition von Visual Studio auswählen, die sich für Ihre Zwecke eignet. |

## <a name="step-3---install-the-visual-studio-installer"></a>Schritt 3: Installieren des Visual Studio-Installers

Führen Sie dann die Bootstrapperdatei aus, um den Visual Studio-Installer zu installieren. Dieses neue, schlanke Installationsprogramm enthält alle Elemente, die Sie zum Installieren und Anpassen von Visual Studio 2017 benötigen.

1.  Doppelklicken Sie in Ihrem Ordner **Downloads** auf die Bootstrapperdatei, die einer der folgenden Dateien entspricht oder ähnelt:

  * **vs_enterprise.exe** für Visual Studio Enterprise
  * **vs_professional.exe** für Visual Studio Professional
  * **vs_community.exe** für Visual Studio Community  <br><br>

  Wenn eine Benachrichtigung der Benutzerkontensteuerung angezeigt wird, klicken Sie auf **Ja**.

2.  Sie werden gebeten, die Microsoft-[Lizenzbedingungen](https://www.visualstudio.com/license-terms/) und die Microsoft-[Datenschutzbestimmungen](https://go.microsoft.com/fwlink/?LinkID=824704) zu akzeptieren. Klicken Sie auf **Weiter**.  

   ![Lizenzbedingungen und Datenschutzbestimmungen](media/vs2017-privacy-and-license-terms.PNG "Microsoft-Lizenzbedingungen und Microsoft-Datenschutzbestimmungen")

## <a name="step-4---select-workloads"></a>Schritt 4: Auswählen der Arbeitsauslastungen

Nach der Installation des Installers können Sie diesen zum Anpassen Ihrer Installation verwenden, indem Sie die Features – oder Arbeitsauslastungen – auswählen, die Sie wünschen. Gehen Sie folgendermaßen vor:

1.  Suchen Sie die gewünschten Arbeitsauslastungen im Bildschirm **Visual Studio wird installiert**.

 ![Auswählen einer Workload aus dem Visual Studio 2017-Setupdialogfeld](../install/media/install-visual-studio-enterprise.png)

     Wählen Sie beispielsweise die Workload „.NET Desktopentwicklung“ aus. Sie wird mit dem standardmäßigen Kern-Editor bereitgestellt, der die grundlegende Codebearbeitung für über 20 Sprachen, die Möglichkeit, Code aus einem beliebigen Ordner heraus zu öffnen und zu bearbeiten, ohne dass ein Projekt erforderlich ist, und die integrierte Quellcodekontrolle unterstützt.  

2.  Nachdem Sie die gewünschten Arbeitsauslastungen ausgewählt haben, klicken Sie auf **Installieren**.

    Als Nächstes werden Statusbildschirme angezeigt, die über den Fortschritt der Installation von Visual Studio informieren.

3.  Nachdem die neuen Arbeitsauslastungen und Komponenten installiert wurden, klicken Sie auf **Starten**.  

> [!TIP]
>  Nach der Installation können Sie jederzeit die Installation von Workloads oder Komponenten nachholen. Wenn Sie Visual Studio geöffnet haben, navigieren Sie zu **Extras** > **Tools und Features abrufen…**. Dadurch wird der Visual Studio-Installer geöffnet. Öffnen Sie den **Visual Studio-Installer** alternativ über das Startmenü. Nun können Sie die Workloads oder Komponenten auswählen, die Sie installieren möchten. Klicken Sie anschließend auf **Ändern**.  

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](media/video-icon.png "Video ansehen")  |    [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171), in dem erläutert wird, wie Sie den Visual Studio-Installer und danach eine Arbeitsauslastung installieren. |

## <a name="step-5---select-individual-components-optional"></a>Schritt 5: Auswählen einzelner Komponenten (optional)

Wenn Sie das Feature für Arbeitsauslastungen nicht zur Anpassung Ihrer Visual Studio-Installation verwenden möchten, können Sie stattdessen auch einzelne Komponenten installieren. Klicken Sie dazu im Visual Studio-Installer auf die Option **Einzelne Komponenten**, wählen Sie die gewünschten Komponenten aus, und folgen Sie den Anweisungen.

  ![Visual Studio 2017: Installieren einzelner Komponenten](media/vs2017-components.PNG "Installieren einzelner Visual Studio-Komponenten")

  |         |         |
  |---------|---------|
  |  ![Kamerasymbol für video](media/video-icon.png "Video ansehen")  |   [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171), in dem gezeigt wird, wie Sie mithilfe des Visual Studio-Installers eine einzelne Komponente installieren. |

## <a name="step-6---install-language-packs-optional"></a>Schritt 6: Installieren von Language Packs (optional)

Standardmäßig versucht das Installationsprogramm bei der ersten Ausführung die Sprache des Betriebssystems zu verwenden. Zum Installieren von Visual Studio 2017 in einer bestimmten Sprache Ihrer Wahl klicken Sie im Visual Studio-Installationsprogramm auf die Option **Language Packs** und folgen den Eingabeaufforderungen.

  ![Visual Studio 2017 - Installieren von Language Packs](media/vs2017-languages.PNG "Installieren von Visual Studio-Language Packs")

  |         |         |
  |---------|---------|
  |  ![Kamerasymbol für video](media/video-icon.png "Video ansehen")  |   [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171), in dem gezeigt wird, wie Sie mithilfe des Visual Studio-Installers ein Sprachpaket installieren. |

### <a name="change-the-installer-language-from-the-command-line"></a>Ändern der Installersprache über die Befehlszeile

Eine andere Möglichkeit zum Ändern der Standardsprache ist die Ausführung des Installers über die Befehlszeile. Mit dem Befehl `vs_installer.exe --locale en-US` können Sie z.B. erzwingen, dass das Installationsprogramm auf Englisch ausgeführt wird. Das Installationsprogramm speichert diese Einstellung für zukünftige Ausführungen. Der Installer unterstützt die folgenden Sprachtoken: zh-CN, zh-TW, cs-CZ, en-US, es-ES, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU und tr-TR.


## <a name="step-7---start-developing"></a>Schritt 7: Mit dem Entwickeln beginnen
1. Klicken Sie nach Abschluss der Visual Studio-Installation auf **Starten**, um mit dem [Programmieren in Visual Studio zu beginnen](../ide/get-started-developing-with-visual-studio.md).

2. Klicken Sie auf **Datei** und dann auf **Neues Projekt**.

3. Wählen Sie einen neuen Projekttyp aus. <br><br>
   Um beispielsweise [eine C++-App zu erstellen](../ide/getting-started-with-cpp-in-visual-studio.md), klicken Sie auf **Installiert**, erweitern Sie **Visual C++**, und wählen Sie dann den C++-Projekttyp aus, den Sie erstellen möchten. <br><br>
   Um [eine C#-App zu erstellen](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), klicken Sie auf **Installiert**, erweitern Sie **Visual C#**, und wählen Sie dann den C#-Projekttyp aus, den Sie erstellen möchten.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch
* [Aktualisieren von Visual Studio 2017](update-visual-studio.md)
* [Ändern von Visual Studio 2017 RC](modify-visual-studio.md)
* [Deinstallieren von Visual Studio 2017](uninstall-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017](visual-studio-administrator-guide.md)
  * [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Installieren von Build Tools in einem Container](build-tools-container.md)
