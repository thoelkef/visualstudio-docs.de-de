---
title: Entwicklung von bewährten Methoden für COM, VSTO und VBA-add-ins in Office
ms.custom: ''
ms.date: 07/25/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 020faeb330348049dcf12431fadfa6ab099d1584
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Entwicklung von bewährten Methoden für COM, VSTO und VBA-add-ins in Office
  Wenn Sie COM, VSTO oder VBA-add-ins für Office entwickeln, führen Sie die Entwicklung bewährten Methoden in diesem Artikel beschrieben.   Dies hilft sicherzustellen:

-  Ihre Add-Ins über verschiedene Versionen und Bereitstellungen von Office-Kompatibilität.
-  Reduzierter Komplexität von Add-in-Bereitstellung für Ihre Benutzer und IT-Administratoren.
-  Unbeabsichtigte Installation oder zur Laufzeit Fehler des add-Ins werden nicht ausgeführt.

>: Hinweis Die [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) Vorbereitung auf den COM-VSTO oder VBA-add-in für Windows Store wird nicht unterstützt. COM, VSTO und VBA-add-ins kann nicht in den Windows Store oder im Office Store verteilt werden. 
  
## <a name="do-not-check-for-office-during-installation"></a>Aktivieren Sie nicht für Office während der installation  
 Wird nicht empfohlen, müssen das Add-in erkennt, ob es sich bei Office während des Installationsvorgangs-Add-in installiert ist. Wenn Office nicht installiert ist, können Sie das Add-In installieren, und der Benutzer wird in der Lage, darauf zugreifen, nachdem Office installiert ist. 
  
## <a name="use-embedded-interop-types-nopia"></a>Verwenden Sie eingebettete Interop-Typen (NoPIA)  
Wenn Ihre Lösung verwendet .NET 4.0 oder höher verwenden eingebettete Interop-Typen (NoPIA) anstelle von abhängig von der Office Primary Interop Assemblys (PIA) redistributable. Mit Typ einbetten reduziert die Installationsgröße der Projektmappe und zukünftige Kompatibilität sichergestellt. Office 2010 ist die letzte Version von Office, die die verteilbare PIA geliefert. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Einbetten von Typinformationen aus Microsoft Office-Assemblys](https://msdn.microsoft.com/en-us/library/ee317478.aspx) und [Typäquivalenz und eingebettete Interop-Typen](/windows/uwp/porting/desktop-to-uwp-root).

Wenn Ihre Lösung eine frühere Version von .NET verwendet, wird empfohlen, dass Sie die Projektmappe zur Verwendung von .NET 4.0 oder höher aktualisieren. Mithilfe von .NET 4.0 oder höher reduziert die Common Language Runtime-Komponenten auf neueren Versionen von Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Abhängig von bestimmten Versionen von Office zu vermeiden  
Die Lösung Funktionalität verwendet, die nur in neueren Versionen von Office verfügbar sind, sicher, dass die Funktion (wenn möglich, auf die Funktionsebene) vorhanden ist zur Laufzeit (z. B. mit Ausnahme behandeln von oder indem Sie die Version überprüfen). Mindestversionen anstelle von bestimmten Versionen, verwenden unterstützten APIs im Objektmodell, z. B. Überprüfen der [Application.Version Eigenschaft](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx). Wird nicht empfohlen, dass Sie auf Office binäre Metadaten, Installationspfade oder Registrierungsschlüssel beruhen, da sich diese zwischen Installationen, Umgebungen und Versionen ändern können.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Aktivieren Sie 32-Bit und 64-Bit-Office-Verwendung   
Der Build-Standardziel sollte (x86) 32-Bit und 64-Bit-(x64) unterstützen, es sei denn, Ihre Lösung von Bibliotheken abhängig ist, die nur für eine bestimmte Bitanzahl verfügbar sind. Die 64-Bit-Version von Office wächst in der Annahme, insbesondere in big Data-Umgebungen. Unterstützung sowohl 32-Bit- und 64-Bit-erleichtert für Ihre Benutzer für den Übergang zwischen 32-Bit und 64-Bit-Versionen von Office.

Beim Schreiben von VBA-Code wird mit 64-Bit-Safe declare-Anweisungen und Variablen nach Bedarf zu konvertieren. Darüber hinaus stellen Sie sicher, dass Dokumente zwischen 32-Bit oder 64-Bit-Versionen von Office ausführen, durch die Bereitstellung von Code für jede Bitanzahl Benutzern gemeinsam genutzt werden können. Weitere Informationen finden Sie unter [64-Bit-Visual Basic for Applications (Übersicht)](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx).

## <a name="support-restricted-environments"></a>Eingeschränkte Unterstützung Umgebungen   
Die Projektmappe sollte keine heraufstufung von Benutzerrechten Konto oder Administrator-Berechtigungen erforderlich. Darüber hinaus muss die Lösung hängt nicht festlegen oder ändern:

- Das aktuelle Arbeitsverzeichnis.
- Verzeichnisse, laden die DLL.
- Der PATH-Variable.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Ändern Sie den Speichervorgang Speicherort der freigegebenen Daten und Einstellungen
Wenn die Lösung besteht aus einem Add-in und ein Prozess, der außerhalb von Office ist, verwenden Sie Anwendungsdatenordner des Benutzers oder der Registrierung für den Austausch von Daten oder Einstellungen zwischen Add-Ins und der externe Prozess. Stattdessen Sie verwenden Sie temporären Ordner des Benutzers, der Ordner "Dokumente" oder der Installationsverzeichnis der Projektmappe.

## <a name="increment-the-version-number-with-each-update"></a>Erhöhen Sie die Versionsnummer mit jedem update
Die Versionsnummer der Binärdateien in der Projektmappe festgelegt und mit jedem Update zu erhöhen. Dies wird erleichtern Benutzern das Identifizieren von Änderungen zwischen verschiedenen Versionen und Kompatibilität zu bewerten.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Geben Sie Informationen zur Unterstützung für die neuesten Versionen von Office
Kunden werden gebeten, ISVs Supportinformationen für ihre COM, VSTO und VBA-add-ins bereitstellen, die in Office ausgeführt werden. Auflisten der explizite Unterstützung Anweisungen hilft Kunden mit Office 365 ProPlus verstehen Bereitschaft Tools an Ihren Support. 

Um Informationen zur Unterstützung für Office-Client-Anwendungen (z. B. Word oder Excel) zu ermöglichen, überprüfen Sie zunächst, dass Ihre Add-Ins in der aktuellen Version von Office ausführen, und zum Bereitstellen von Updates, wenn Ihr Add-in in einer zukünftigen Version unterbricht anschließend einen commit. Sie müssen nicht Ihre Add-Ins zu testen, wenn Microsoft einen neuen Build oder ein Update für Office frei. Microsoft sich nur selten ändert, die COM, VSTO und VBA-Erweiterbarkeit-Plattform in Office, und diese Änderungen angemessen dokumentiert.

>Wichtig: Microsoft verwaltet eine Liste der unterstützten-add-ins für Berichte zur hardwarebereitschaft und ISV-Kontaktinformationen. Um das Add-in aufgeführten zu erhalten, finden Sie unter [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Verwenden von Monitor "Prozess", um Installations- oder laden die Probleme Debuggen
Wenn Ihr Add-in Kompatibilitätsprobleme während der Installation oder Load verfügt, beispielsweise kann sie Probleme mit der Datei oder ein Registrierungsschlüsselwert Zugriff verknüpft sein. Verwendung [Prozessmonitor](/sysinternals/downloads/procmon) oder eine ähnliche Debugtool, sich anzumelden, und vergleichen das Verhalten für eine arbeitsumgebung, um das Problem zu identifizieren.
