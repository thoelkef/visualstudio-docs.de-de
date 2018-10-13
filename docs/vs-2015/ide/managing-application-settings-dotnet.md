---
title: Verwalten von Anwendungseinstellungen (.NET) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb2623c9122b987d8e0fe781b62127cd65bde0dc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289509"
---
# <a name="managing-application-settings-net"></a>Verwalten von Anwendungseinstellungen (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Anwendungseinstellungen ermöglichen ein dynamisches Speichern von Anwendungsinformationen. Mit Einstellungen können Sie Informationen über den Clientcomputer speichern, die nicht im Anwendungscode enthalten sein sollen (beispielsweise eine Verbindungszeichenfolge). Außerdem können Benutzereinstellungen und andere zur Laufzeit benötigte Informationen gespeichert werden.  
  
 Durch Anwendungseinstellungen werden die dynamischen Eigenschaften ersetzt, die in früheren Versionen von Visual Studio verwendet wurden.  
  
 Jede Anwendungseinstellung muss einen eindeutigen Namen haben. Dieser Name kann aus einer beliebigen Kombination aus Buchstaben, Zahlen und Unterstrichen bestehen. Er darf jedoch nicht mit einer Zahl beginnen, und er darf keine Leerzeichen enthalten. Der Name kann über die `Name` -Eigenschaft geändert werden.  
  
 Anwendungseinstellungen können als beliebiger Datentyp gespeichert werden, der in XML serialisierbar ist oder über einen `TypeConverter` mit einer Implementierung von `ToString`/`FromString`verfügt. Die geläufigsten Typen lauten `String`, `Integer`und `Boolean`. Sie können Werte jedoch auch als <xref:System.Drawing.Color>, <xref:System.Object>oder als Verbindungszeichenfolge speichern.  
  
 Anwendungseinstellungen enthalten auch einen Wert. Der Wert wird über die Eigenschaft **Wert** festgelegt und muss mit dem Datentyp der Einstellung übereinstimmen.  
  
 Außerdem können Anwendungseinstellungen zur Entwurfszeit an die Eigenschaft eines Formulars oder Steuerelements gebunden werden.  
  
 Es gibt zwei Typen von Anwendungseinstellungen, die sich hinsichtlich ihres Gültigkeitsbereichs unterscheiden:  
  
-   Anwendungsspezifische Einstellungen können für Informationen wie die URL eines Webdiensts oder eine Datenbankverbindungszeichenfolge verwendet werden. Diese Werte werden der Anwendung zugeordnet. Deshalb können Benutzer sie zur Laufzeit nicht ändern.  
  
-   Benutzerspezifische Einstellungen können für Informationen, z. B. die Beibehaltung der letzten Position eines Formulars oder eine Schriftarteinstellung, verwendet werden. Die Benutzer können diese Werte zur Laufzeit ändern.  
  
 Sie können den Typ einer Einstellung mit der Eigenschaft **Bereich** ändern.  
  
 Das Projektsystem speichert die Anwendungseinstellungen in zwei XML-Dateien: in der Datei app.config, die zur Entwurfszeit erstellt wird, wenn Sie die erste Anwendungseinstellung erstellen, sowie in der Datei user.config, die zur Laufzeit erstellt wird, wenn der die Anwendung ausführende Benutzer den Wert einer Benutzereinstellung ändert. Beachten Sie, dass Änderungen in den Benutzereinstellungen nicht auf die Festplatte geschrieben werden, es sei denn, die Anwendung ruft ausdrücklich eine Methode auf, die dies veranlasst.  
  
## <a name="creating-application-settings-at-design-time"></a>Erstellen von Anwendungseinstellungen zur Entwurfszeit  
 Zur Entwurfszeit können Anwendungseinstellungen auf zwei Arten erstellt werden: im **Projekt-Designer** über die Seite **Einstellungen**oder für ein Formular oder ein Steuerelement über das **Eigenschaftenfenster** , in dem Sie eine Einstellung an eine Eigenschaft binden können.  
  
 Beim Erstellen einer anwendungsspezifischen Einstellung (z. B. einer Datenbankverbindungszeichenfolge oder eines Verweises auf Serverressourcen) speichert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diese Einstellung in app.config mit dem `<applicationSettings>` -Tag. (Verbindungszeichenfolgen werden unter dem `<connectionStrings>` -Tag gespeichert.)  
  
 Beim Erstellen einer benutzerspezifischen Einstellung (z. B. einer Standardschriftart, Startseite oder Fenstergröße) speichert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diese Einstellung in app.config mit dem `<userSettings>` -Tag.  
  
> [!IMPORTANT]
>  Beim Speichern von Verbindungszeichenfolgen in app.config sollten Sie Vorsichtsmaßnahmen treffen, damit keine vertraulichen Informationen, etwa Kennwörter oder Serverpfade, in der Verbindungszeichenfolge preisgegeben werden.  
>   
>  Wenn Sie Informationen für Verbindungszeichenfolgen aus einer externen Quelle übernehmen (z. B. bei Eingabe einer Benutzer-ID und eines Kennworts durch einen Benutzer), müssen Sie sicherstellen, dass die Werte zum Aufbau der Verbindungszeichenfolge keine zusätzlichen Parameter für Verbindungszeichenfolgen enthalten, die das Verhalten der Verbindung ändern oder ihre Sicherheit gefährden.  
>   
>  Verwenden Sie am besten die geschützte Konfiguration, um vertrauliche Informationen in der Konfigurationsdatei zu verschlüsseln. Weitere Informationen finden Sie unter [Schützen von Verbindungsinformationen](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
> [!NOTE]
>  Da für Klassenbibliotheken das Modell der Konfigurationsdateien nicht verwendet wird, gelten Anwendungseinstellungen nicht für Klassenbibliotheksprojekte. Ausgenommen hiervon sind DLL-Projekte in Visual Studio Tools for Office, die über Konfigurationsdateien verfügen können.  
  
## <a name="using-customized-settings-files"></a>Verwenden von benutzerdefinierten Einstellungsdateien  
 Sie können dem Projekt zur einfachen Verwaltung von Einstellungsgruppen benutzerdefinierte Einstellungsdateien hinzufügen. Einstellungen, die in einer Datei enthalten sind, werden als Einheit geladen und gespeichert. Durch das Speichern von häufig und weniger häufig verwendeten Einstellungsgruppen in separaten Dateien können Sie beim Laden und Speichern von Einstellungen Zeit sparen.  
  
 Beispielsweise können Sie dem Projekt eine Datei namens SpecialSettings.settings hinzufügen. Die `SpecialSettings` -Klasse wird zwar im `My` -Namespace nicht verfügbar gemacht, mit **Code anzeigen** kann jedoch die benutzerdefinierte Einstellungsdatei, die `Partial Class SpecialSettings`enthält, gelesen werden.  
  
 Zunächst sucht der Einstellungs-Designer nach der vom Projektsystem erstellten Datei Settings.settings. Dies ist die Standarddatei, die im Projekt-Designer auf der Registerkarte **Einstellungen** angezeigt wird. Settings.settings befindet sich bei [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] -Projekten im Ordner My Project und bei [!INCLUDE[csprcs](../includes/csprcs-md.md)] -Projekten im Ordner Properties. Der Projekt-Designer sucht dann nach anderen Einstellungsdateien im Stammordner des Projekts. Deshalb sollten Sie die benutzerdefinierte Einstellungsdatei dort ablegen. Wenn Sie die Einstellungsdatei einem anderen Projektordner hinzufügen, findet der Projekt-Designer sie nicht.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Ändern von Anwendungseinstellungen zur Laufzeit nach entsprechendem Zugriff in Visual Basic  
 In [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] -Projekten können Sie mit dem `My.Settings` -Objekt zur Laufzeit auf Anwendungseinstellungen zugreifen. Klicken Sie auf der Seite **Einstellungen** auf die Schaltfläche **Code anzeigen** , um die Datei Settings.vb anzuzeigen. Settings.vb definiert die `Settings` -Klasse, sodass Sie die folgenden Ereignisse für die Settings-Klasse handhaben können: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>und <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Beachten Sie, dass die `Settings` -Klasse in der Datei Settings.vb eine partielle Klasse ist, die nur den im Besitz des Benutzers befindlichen Code anzeigt und nicht die gesamte generierte Klasse. Weitere Informationen über den Zugriff auf Anwendungseinstellungen über das `My.Settings` -Objekt finden Sie unter [Accessing Application Settings](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)verfügt.  
  
 Die Werte aller benutzerspezifischen Einstellungen, die der Benutzer zur Laufzeit ändert (z. B. die Position eines Formulars), werden in der Datei user.config gespeichert. Beachten Sie, dass die Standardwerte weiterhin in app.config gespeichert sind.  
  
 Wenn benutzerspezifische Einstellungen zur Laufzeit geändert wurden, z. B. beim Testen der Anwendung, und Sie diese Einstellungen auf die Standardwerte zurücksetzen möchten, klicken Sie auf die Schaltfläche **Synchronisieren** .  
  
 Es wird dringend empfohlen, dass Sie mit dem `My.Settings` -Objekt und der standardmäßigen SETTINGS-Datei auf Einstellungen zugreifen. Dies ist deshalb wichtig, da mit dem Einstellungs-Designer den Einstellungen Eigenschaften zugewiesen werden können und Benutzereinstellungen vor dem Beenden der Anwendung automatisch gespeichert werden. Die [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] -Anwendung kann jedoch direkt auf Einstellungen zugreifen. In diesem Fall müssen Sie die `MySettings` -Klasse aufrufen und eine benutzerdefinierte Einstellungsdatei im Stammordner des Projekts verwenden. Außerdem müssen Sie die Benutzereinstellungen wie bei einer C#-Anwendung vor dem Beenden der Anwendung speichern. Informationen hierzu finden Sie im folgenden Abschnitt.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Ändern von Anwendungseinstellungen zur Laufzeit nach entsprechendem Zugriff in Visual C#  
 In anderen Programmiersprachen als [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], z. B. [!INCLUDE[csprcs](../includes/csprcs-md.md)], müssen Sie direkt auf die `Settings` -Klasse zugreifen. Dies ist im folgenden [!INCLUDE[csprcs](../includes/csprcs-md.md)] -Beispiel veranschaulicht.  
  
```csharp  
Properties.Settings.Default.FirstUserSetting = "abc";  
```  
  
 Sie müssen die `Save` -Methode dieser Wrapperklasse explizit aufrufen, damit die Benutzereinstellungen erhalten bleiben. Hierfür verwenden Sie normalerweise den `Closing` -Ereignishandler des Hauptformulars. Das folgende [!INCLUDE[csprcs](../includes/csprcs-md.md)] -Beispiel zeigt einen Aufruf der `Save` -Methode.  
  
```csharp  
Properties.Settings.Default.Save();  
```  
  
 Allgemeine Informationen über das Zugreifen auf Anwendungseinstellungen über die Klasse `Settings` finden Sie unter [Übersicht über Anwendungseinstellungen](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Informationen über das Durchlaufen der Einstellungen finden Sie in diesem [Forumsbeitrag](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Anwendungseinstellungen](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)



