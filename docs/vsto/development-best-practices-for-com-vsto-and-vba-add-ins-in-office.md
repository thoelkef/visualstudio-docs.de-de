---
title: Bewährte Entwicklungsmethoden für COM, VSTO und VBA-add-ins in Office
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
ms.openlocfilehash: bf00afb612e12ce6712206808897a3b851d68b3a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671864"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Bewährte Entwicklungsmethoden für COM, VSTO und VBA-add-ins in Office
  Wenn Sie COM, VSTO oder VBA-add-ins für Office entwickeln, führen Sie die besten Entwicklungsmethoden in diesem Artikel beschrieben.   Dadurch wird sichergestellt:

-  Kompatibilität von Add-Ins über verschiedene Versionen und Bereitstellungen von Office.
-  Geringere Komplexität der Add-in-Bereitstellung für Ihre Benutzer und IT-Administratoren.
-  Unbeabsichtigte Installation oder zur Laufzeit Fehler des add-Ins werden nicht ausgeführt.

>: Hinweis Die [Desktop-Brücke](/windows/uwp/porting/desktop-to-uwp-root) Vorbereitung auf den COM-VSTO oder VBA-add-in für den Windows Store wird nicht unterstützt. COM, VSTO und VBA-add-ins können nicht in den Windows Store oder den Office Store verteilt werden. 
  
## <a name="do-not-check-for-office-during-installation"></a>Aktivieren Sie nicht für Office während der installation  
 Müssen das Add-in erkennt, ob es sich bei Office installiert ist, während der Add-in-Installation empfohlen nicht. Wenn Office nicht installiert ist, können Sie das Add-in installieren, und der Benutzer wird in der Lage, darauf zuzugreifen, nachdem Office installiert ist. 
  
## <a name="use-embedded-interop-types-nopia"></a>Verwenden Sie die eingebettete Interop-Typen (NoPIA)  
Wenn Ihre Lösung verwendet .NET 4.0 oder höher verwenden eingebettete interop-Typen (NoPIA) anstelle von abhängig von der Office Primary Interop Assemblies (PIA) redistributable. Verwenden das Einbetten von Typen reduziert die Installationsgröße der Lösung und zukünftige Kompatibilität sichergestellt. Office 2010 ist die letzte Version von Office, die die verteilbare PIA geliefert wurden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Einbetten von Typinformationen aus Microsoft Office-Assemblys](https://msdn.microsoft.com/library/ee317478.aspx) und [Typäquivalenz und eingebettete interop-Typen](/windows/uwp/porting/desktop-to-uwp-root).

Wenn Ihre Lösung auf eine frühere Version von .NET verwendet, empfehlen wir, dass Sie die Projektmappe, um .NET 4.0 oder höher verwenden, aktualisieren. Mithilfe von .NET 4.0 oder höher reduziert die Common Language Runtime von erforderlichen Komponenten auf neuere Versionen von Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Vermeiden Sie abhängig von bestimmten Versionen von Office  
Ihre Lösung Funktionalität verwendet, die nur in neueren Versionen von Office verfügbar sind, sicher, dass die Funktion (wenn möglich, auf die Feature-Ebene) vorhanden ist. zur Laufzeit (z. B. mit der Ausnahme Ausnahmebehandlungsfehler oder indem Sie die Version überprüfen). Überprüfen Sie Mindestversionen, statt in bestimmten Versionen, wie z. B. die unterstützten APIs im Objektmodell, mit der [Application.Version Eigenschaft](https://msdn.microsoft.com/library/office/microsoft.office.interop.excel._application.version.aspx). Es wird nicht empfohlen, dass Sie auf Office binary Metadaten, Installationspfade oder Registrierungsschlüssel verlassen, da diese Installationen, Umgebungen und Versionen ändern können.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Aktivieren Sie die 32-Bit- und 64-Bit-Office-Nutzung   
Ihr Build-Standardziel sollte sowohl für 32-Bit-(x86) als auch für 64-Bit-(x64) unterstützen, es sei denn, Ihre Lösung von Bibliotheken abhängig ist, die nur für eine bestimmte Bitanzahl verfügbar sind. Die 64-Bit-Version von Office zunehmen bei Einführung, insbesondere in big Data-Umgebungen. Unterstützung sowohl für 32-Bit-als auch für 64-Bit-erleichtert Ihnen für Ihre Benutzer für den Übergang zwischen 32-Bit und 64-Bit-Versionen von Office.

Beim Schreiben von VBA-Code wird mit 64-Bit-Safe declare-Anweisungen und Variablen nach Bedarf zu konvertieren. Darüber hinaus stellen Sie sicher, dass Dokumente Benutzer, die entweder 32-Bit oder 64-Bit-Versionen von Office ausführen, indem Sie Code für jede Bitanzahl für das Bereitstellen gemeinsam genutzt werden können. Weitere Informationen finden Sie unter [VBA-64-Bit-Anwendungen (Übersicht)](https://msdn.microsoft.com/library/office/gg264421.aspx).

## <a name="support-restricted-environments"></a>Zur Unterstützung von eingeschränkter Umgebungen   
Ihre Lösung sollte keine Rechte heraufstufung von Benutzerrechten-Konto oder Administratorrechte erfordern. Darüber hinaus sollte die Lösung nicht abhängig festlegen oder ändern:

- Das aktuelle Arbeitsverzeichnis.
- Verzeichnisse, laden die DLL.
- Der PATH-Variablen.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Ändern Sie den Speichervorgang Speicherort der freigegebenen Daten und Einstellungen
Wenn die Lösung besteht aus einem Add-in und ein Prozess, der außerhalb von Office ist, verwenden Sie nicht Anwendungsdatenordner des Benutzers oder der Registrierung zum Austauschen von Daten oder Einstellungen zwischen dem Add-in und der externe Prozess. Stattdessen Sie verwenden Sie temporären Ordner des Benutzers, den Ordner "Dokumente" und den Installationsverzeichnis der Projektmappe.

## <a name="increment-the-version-number-with-each-update"></a>Erhöht die Versionsnummer bei jeder Aktualisierung
Die Versionsnummer der Binärdateien in der Projektmappe festgelegt, und es mit jedem Update erhöht. Dies veranlasst er für Benutzer einfacher, Änderungen zwischen den Versionen ermitteln und Bewerten der Kompatibilität.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Geben Sie Informationen zur Unterstützung bei den neuesten Versionen von Office
Kunden werden gebeten, ISVs, Informationen zur Unterstützung für die COM, VSTO und VBA-add-ins bieten, die in Office ausgeführt. Ihre explizite Unterstützung-Anweisungen können Kunden mithilfe von Office 365 ProPlus auflisten verstehen bereitschaftstools Ihre Unterstützung. 

Um Unterstützung für Office-Clientanwendungen (z. B. Word oder Excel) bereitzustellen, überprüfen Sie zunächst, dass Ihre Add-Ins in der aktuellen Office-Version ausgeführt, und dann einen Commit ausführen, um die Bereitstellung von Updates, wenn das Add-in in einer zukünftigen Version aufgehoben. Sie müssen keine Add-Ins zu testen, wenn Microsoft einen neuen Build oder ein Update für Office veröffentlicht. Microsoft nur selten ändert, die COM, VSTO und VBA-Plattform in Office-Erweiterbarkeit, und diese Änderungen werden gut dokumentiert.

>Wichtig: Microsoft verwaltet eine Liste der unterstützten-add-ins für Berichte zur hardwarebereitschaft und ISV-Kontaktinformationen. Das add-in aufgelistet finden Sie unter [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Verwenden Sie Monitor "Prozess", um Installations- oder laden die Probleme zu debuggen
Verfügt Ihr Add-in Kompatibilitätsprobleme während der Installation oder laden, können sie Probleme mit Datei-oder Registrierungszugriff zugeordnet werden. Verwendung [Process Monitor](/sysinternals/downloads/procmon) oder ähnliche Debugtool, sich anzumelden, und Vergleichen von Verhalten in einer arbeitsumgebung, um das Problem zu identifizieren.
