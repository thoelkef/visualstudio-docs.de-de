---
title: "Installieren von Visual Studio 2017 RC | Microsoft-Dokumentation"
description: "Erfahren Sie Schritt für Schritt, wie Sie Visual Studio installieren."
ms.custom: 
ms.date: 11/18/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio Preview
- install Visual Studio
- installing Visual Studio
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
translationtype: Human Translation
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 997a1e0966c5e08314c616dba76842120ab50d63

---
# <a name="install-visual-studio-2017-rc"></a>Installieren von Visual Studio 2017 RC
Willkommen Sie bei einer neuen Möglichkeit zur Installation von Visual Studio. Mit unserer neuesten Version können Sie nun ganz einfach nur die Funktionen auswählen und installieren, die Sie benötigen. Gleichzeitig wurde der Mindestspeicherplatz für Visual Studio reduziert, sodass die Installation schneller erfolgt und mit geringerer Beeinträchtigung des Systems verbunden ist, als je zuvor.  

 Sie möchten mehr zu weiteren Neuerungen in RC wissen? Sehen Sie sich die [Anmerkungen zur Version](https://www.visualstudio.com/news/releasenotes/vs15-relnotes) an. Ausführlichere Informationen zum neuen Design der Installationsumgebung finden Sie in den Blogbeiträgen „[Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)“ (Der schnellere und schlankere Visual Studio-Installer) sowie „[Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)“ (Anatomie einer Visual Studio-Installation mit geringen Auswirkungen).  

 Bereit für die Installation? Schauen Sie sich diese schrittweise Vorführung an. Fangen wir also an.  

## <a name="install-the-installer"></a>Installieren des Installationsprogramms  
 Wenn Sie Visual Studio 2017 RC herunterladen, erhalten Sie eine Bootstrapperdatei, die wiederum das neue Lightweight-Installationsprogramm installiert. Dieses neue Installationsprogramm enthält alles, was Sie benötigen, um Ihre Installation anzupassen.  

> [!IMPORTANT]
> Wenn Sie über ein Vorschaurelease von Visual Studio 2017 auf Ihrem Computer verfügen, werden Sie aufgefordert, dieses vor der Installation von Visual Studio 2017 RC zu entfernen.

1.  [Laden Sie Visual Studio Enterprise 2017 RC herunter](https://www.visualstudio.com/vs/visual-studio-2017-rc/), und klicken Sie auf **Speichern**.  Führen Sie dann aus dem Ordner **Downloads** heraus die Datei `vs_Enterprise.exe` aus.  

     Wenn eine Benachrichtigung der Benutzerkontensteuerung angezeigt wird, klicken Sie auf **Ja**.  

2.  Sie werden gebeten, die Microsoft-[Lizenzbedingungen](https://www.visualstudio.com/support/legal/mt591984) und die Microsoft-[Datenschutzbestimmungen ](https://www.visualstudio.com/dn948229) zu akzeptieren. Klicken Sie auf **Installieren**, um den Vorgang fortzusetzen.  

  ![Lizenzbedingungen und Datenschutzbestimmungen](media/01-installingdev15prev4-licensetermsandprivacystatement.png "Microsoft-Lizenzbedingungen und Microsoft-Datenschutzbestimmungen")  

3.  Es werden mehrere Statusbildschirme angezeigt, die den Fortschritt der Installation anzeigen. Nach Abschluss der Installation können Sie die gewünschten Featuregruppen (oder Arbeitsauslastungen) auswählen.

## <a name="install-workloads"></a>Installieren von Arbeitsauslastungen  
 Jetzt können Sie Ihre Installation mithilfe von Arbeitsauslastungen anpassen. Wählen Sie eine oder mehrere der gewünschten Arbeitsauslastungen aus. Jede Arbeitsauslastung enthält die Features, die Sie für die bevorzugte Programmiersprache oder Plattform benötigen.  

 Führen Sie dazu folgende Schritte aus:  

1.  Suchen Sie die gewünschten Arbeitsauslastungen im Bildschirm **Visual Studio wird installiert**.  

  ![Visual Studio 2017 RC-Setupdialogfeld](../ide/media/willow1.png "Visual Studio 2017 wird installiert")

     Wählen Sie beispielsweise die Arbeitsauslastung für .NET Desktop-Entwicklung aus. Sie wird mit dem standardmäßigen Kern-Editor bereitgestellt, der die grundlegende Codebearbeitung für über 20 Sprachen, die Möglichkeit, Code aus einem beliebigen Ordner heraus zu öffnen und zu bearbeiten, ohne dass ein Projekt erforderlich ist, und die integrierte Quellcodekontrolle unterstützt.  

2.  Nachdem Sie die gewünschten Arbeitsauslastungen ausgewählt haben, klicken Sie auf **Installieren**.  

    Als Nächstes werden Statusbildschirme angezeigt, die über den Fortschritt der Installation von Visual Studio informieren.

3.  Nachdem die neuen Arbeitsauslastungen und Komponenten installiert wurden, klicken Sie auf **Starten**.

## <a name="install-individual-components"></a>Installieren einzelner Komponenten

Wenn Sie das praktische Arbeitsauslastungsfeature zum Anpassen Ihrer Visual Studio-Installation nicht verwenden möchten, klicken Sie im Visual Studio-Installer auf die Option **Einzelne Komponenten**, wählen Sie die gewünschten Komponenten aus, und folgen Sie den Anweisungen.

  ![Visual Studio 2017: Installieren einzelner Komponenten](media/vs2017install-IndividualComponents.PNG "Installieren einzelner Visual Studio-Komponenten")

## <a name="install-language-packs"></a>Installieren von Language Packs

Zum Installieren von Visual Studio 2017 RC in einer bestimmten Sprache Ihrer Wahl klicken Sie im Visual Studio-Installer auf die Option **Language Packs**, und folgen den Eingabeaufforderungen.

  ![Visual Studio 2017 - Installieren von Language Packs](media/vs2017install-LanguagePacks.PNG "Installieren von Visual Studio-Language Packs")

### <a name="change-the-installer-language"></a>Ändern der Sprache des Installationsprogramms

Standardmäßig versucht das Installationsprogramm bei der ersten Ausführung die Sprache des Betriebssystems zu verwenden. Das Installationsprogramm speichert diese Einstellung. Sie können die Einstellung ändern, indem Sie das Installationsprogramm über die Befehlszeile ausführen. Mit dem Befehl `vs_installer.exe --locale en-US` können Sie z.B. erzwingen, dass das Installationsprogramm auf Englisch ausgeführt wird. Diese Einstellung wird beim nächsten Ausführen des Installationsprogramms wieder verwendet. Das Installationsprogramm unterstützt die folgenden Sprachtoken: zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES und tr-TR.


  > [!IMPORTANT]
  > Während Visual Studio 2017 RC im Allgemeinen für die Verwendung in einer Produktionsumgebung unterstützt wird, werden die Arbeitsauslastungen und Komponenten, die in der Benutzeroberfläche der Installation als „Vorschau“ gekennzeichnet sind, nicht für die Verwendung in einer Produktionsumgebung unterstützt.

## <a name="see-also"></a>Siehe auch  
* [Ändern von Visual Studio 2017 RC](modify-visual-studio.md)
* [Deinstallieren von Visual Studio 2017 RC](uninstall-visual-studio.md)
* [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
* [Melden eines Problems mit Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)



<!--HONumber=Feb17_HO4-->


