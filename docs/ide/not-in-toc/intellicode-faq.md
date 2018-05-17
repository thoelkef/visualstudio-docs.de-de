---
title: 'IntelliCode: Häufig gestellte Fragen'
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: a077aae7104d1e8b96fdebffd70355a05daa19f4
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# Visual Studio IntelliCode: Häufig gestellte Fragen

Vielen Dank für Ihr Interesse an Visual Studio IntelliCode. Dieses kurze FAQ beantwortet einige Fragen, die Sie sich möglicherweise stellen.

## F. Was ist Visual Studio IntelliCode?

Visual Studio IntelliCode ist eine neue Funktion, die bei der Entwicklerkonferenz Build 2018 angekündigt wurde und die Softwareentwicklung mithilfe von künstlicher Intelligenz verbessert. IntelliCode hilft Entwicklern und Teams dabei, zuverlässig zu codieren, Probleme schneller zu ermitteln und sich auf Code Reviews zu konzentrieren.

In einer frühen Veranschaulichung wurde gezeigt, wie IntelliCode den Softwareentwicklungsprozess auf folgende Weise verbessert:

- Übermittelt kontextabhängige Codevervollständigungen
- Hilft Entwicklern dabei, sich an die Muster und Konventionen ihres Teams zu halten
- Sucht nach schwer auffindbaren Codeproblemen
- Legt den Schwerpunkt auf Code Reviews, indem die Aufmerksamkeit auf die wichtigen Bereiche gerichtet wird.

Unter [https://aka.ms/intellicode](https://aka.ms/intellicode) können Sie weitere Informationen finden und sich für Neuigkeiten und private Vorschauen anmelden.

## F. Was ermöglicht Visual Studio IntelliCode den Kunden?

Visual Studio IntelliCode verfügt über eine Reihe von Funktionen, die mithilfe von künstlicher Intelligenz (KI) neue Produktivitätserweiterungen anbieten.

Entwickler können für Visual Studio 2017 Version 15.7 und höher [eine experimentelle Erweiterung herunterladen](https://go.microsoft.com/fwlink/?linkid=872707). Die Erweiterung bietet erweitertes IntelliSense, die für den Entwickler die API vorhersieht, die wahrscheinlich am besten zur Verwendung geeignet ist, anstatt nur eine alphabetische Liste der Member darzustellen. Sie verwendet den aktuellen Codekontext und Muster des Entwicklers, um diese dynamische Liste bereitzustellen. Die Erweiterung wird in den nächsten Monaten mit weiteren Funktionen ausgestattet.

## F: Was macht „KI-unterstütztes IntelliSense“, das von IntelliCode unterstützt wird, besser als reguläres IntelliSense?

Mit IntelliCode schlägt die Vervollständigungsliste das wahrscheinlich richtige API für einen Entwickler vor, anstatt eine einfache alphabetische Liste der Member anzuzeigen. Es verwendet den aktuellen Codekontext des Entwicklers und Muster, die auf 2000 qualitativ hochwertigen Open-Source-Projekten auf GitHub mit jeweils über 100 Sternen basieren, um diese dynamische Liste bereitzustellen. Die Ergebnisse bilden ein Modell, das die wahrscheinlichsten und relevantesten API-Aufrufe vorhersagt.

## F. Was ist die Zukunft von IntelliCode?

Eine Vielzahl von Möglichkeiten zur Verbesserung der Produktivität von Entwicklern mithilfe von KI und anderen fortgeschrittenen Verfahren. Bei der Entwicklerkonferenz Build 2018 wurde eine frühe Übersicht zu einigen Szenarios veranschaulicht, bei denen die künstliche Intelligenz Entwicklern helfen kann, aber es gibt noch viele mehr. Wir sind daran interessiert, von Entwicklern zu lernen, die damit experimentieren, melden Sie sich also für Neuigkeiten und Updates unter [https://aka.ms/intellicode](https://aka.ms/intellicode) an.

## F. Wie viel kostet es?

Es gibt derzeit noch keine Ankündigungen zu den Preisen.

## F. Wann wird IntelliCode veröffentlicht?

Das KI-unterstützte IntelliSense von IntelliCode befindet sich derzeit in der ersten experimentellen Vorschauversion. Die experimentelle Erweiterung wird weiterhin aktualisiert, und weitere Funktionen werden hinzugefügt. Es gibt keinen Zeitplan für eine endgültige Veröffentlichung, aber wir freuen uns über Feedback von Entwicklern, damit die bestmöglichen Features geboten werden können. Unter [https://aka.ms/intellicode](https://aka.ms/intellicode) können Sie sich für Neuigkeiten und Updates anmelden.

## F. Ist dieses Feature nur in Visual Studio verfügbar?

Das Feature wurde bei der Entwicklerkonferenz Build 2018 in Visual Studio 2017 auf einer C#-Codebase gezeigt. Allerdings freuen wir uns darauf, IntelliCode für weitere Sprachen und Tools in der Visual Studio-Familie zu erweitern.

## F: Wie sieht es mit dem Datenschutz aus? Senden Sie meinen Code an die Cloud? Welche Kundendaten werden an Microsoft gesendet?

Entwickler sind dazu eingeladen, Visual Studio IntelliCode noch heute als experimentelle Vorschauerweiterung kennenzulernen. Der Zweck dieser Erweiterung ist es, den Entwicklern zu ermöglichen, die Funktionen von IntelliCode zu testen und Feedback an das Produktteam zu senden.

Wir erfassen einige anonymisierte Daten zur Verwendung und Fehlerberichtserstattung der Erweiterung, um das Produkt zu verbessern. Es wird kein benutzerdefinierter Code an Microsoft gesendet, aber wir sammeln Informationen über Ihre Verwendung der IntelliCode-Ergebnisse. Die Daten enthalten nur die Open-Source- und .NET-Typen und -Members, die Sie aus der Liste der vorgeschlagenen Ergebnisse von IntelliCode ausgewählt haben. Entwickler können die Datensammlung für Visual Studio deaktivieren, wodurch auch die Datensammlung für die IntelliCode-Erweiterung deaktiviert wird. Klicken Sie dazu in der Menüleiste auf **Hilfe** > **Feedback senden** > **Einstellungen**. Wählen Sie im Dialogfeld **Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio** **Nein, ich möchte nicht teilnehmen** aus, und klicken Sie dann auf **OK**.

Die IntelliCode-Erweiterung fragt möglicherweise regelmäßig nach, ob der Entwickler an einer anonymen Umfrage teilnehmen möchte. Benutzer können sich für Neuigkeiten und eine zukünftige private Vorschau anmelden, derzeit ist dies jedoch keine Voraussetzung, um die experimentelle Erweiterung verwenden zu können.

Zukünftige Features erfordern möglicherweise den Zugriff auf einen Dienst, der eine Anmeldung erfordert. Weitere Informationen werden veröffentlicht, wenn diese Features bereit für die private Vorschauversion sind.