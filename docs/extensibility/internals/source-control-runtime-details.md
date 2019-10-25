---
title: Lauf Zeit Details der Quell Code Verwaltung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d2469bc25fabd9659e09d6ca841ebc44a743cca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723407"
---
# <a name="source-control-runtime-details"></a>Laufzeitdetails für die Quellcodeverwaltung
Ein Projekt wird der Quell Code Verwaltung hinzugefügt, wenn der Benutzer der Quell Code Verwaltung eine Datei im Projekt hinzufügt, oder über einen Automatisierungs Controller, z. b. einen Assistenten. Ein Projekt gibt nicht für sich selbst an, dass es sich unter Quell Code Verwaltung befindet. die Quell Code Verwaltung wird unterstützt, muss aber manuell hinzugefügt werden.

## <a name="registering-with-a-source-control-package"></a>Registrieren mit einem Quell Code Verwaltungspaket
 Wenn eine Datei in Ihrem Projekt zur Quell Code Verwaltung hinzugefügt wird, ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> auf, um Ihnen vier nicht transparente Zeichen folgen zur Verfügung zu stellen, die vom Quell Code Verwaltungssystem als Cookies verwendet werden. Speichern Sie diese Zeichen folgen in der Projektdatei. Diese Zeichen folgen müssen an den Quellcodeverwaltungs-Stub (die Visual Studio-Komponente, die Quell Code Verwaltungs Pakete verwaltet) beim Start des Projekt Typs durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> weitergegeben werden. Dies wiederum lädt das entsprechende Quell Code Verwaltungspaket und leitet den-Befehl an die Implementierung von `IVsSccManager2::RegisterSccProject` weiter.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)