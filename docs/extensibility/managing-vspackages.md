---
title: Verwalten von VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702651"
---
# <a name="manage-vspackages"></a>Verwalten von VSPackages
In den meisten Fällen müssen Sie sich keine Gedanken über die Verwaltung von VSPackages machen, da sich die Projekt- und Elementvorlagen registrieren und das Paket automatisch laden. Unter bestimmten Umständen müssen Sie jedoch möglicherweise etwas mehr lernen, um Ihr Paket zu verwalten.

## <a name="use-the-experimental-instance"></a>Verwenden der experimentellen Instanz
 Weitere Informationen zur experimentellen Instanz finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>VSPackages registrieren und abmelden
 Informationen zum Registrieren und Aufheben der Registrierung von VSPackages und anderen Erweiterungstypen finden Sie unter [Registrieren und Aufheben der Registrierung](../extensibility/registering-and-unregistering-vspackages.md)von VSPackages .

## <a name="load-a-vspackage"></a>VsPackage laden
 VSPackages kann auf autoload eingestellt werden, wenn eine bestimmte CMDUICONTEXT GUID aktiviert ist. Weitere Informationen finden Sie unter Laden von [VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund
 Die `AsyncPackage` Klasse ermöglicht das Laden von Paketen in einem Hintergrundthread für eine bessere Benutzeroberflächenreaktion in Visual Studio. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von AsyncPackage zum Laden](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)von VSPackages im Hintergrund .

## <a name="rule-based-ui-context-for-extensions"></a>Regelbasierter UI-Kontext für Erweiterungen
 Regelbasierte UI-Kontexte ermöglichen es Erweiterungsautoren, die genauen Bedingungen zu definieren, unter denen ein UI-Kontext aktiviert und zugeordnete VSPackages geladen werden. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des regelbasierten UI-Kontexts für Visual Studio-Erweiterungen](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Leistung der Diagnoseerweiterung
Erweiterungen können sich auf die Start- und Lösungslastleistung auswirken. Erfahren Sie, wie die Auswirkungen der Visual Studio-Erweiterung berechnet werden und wie sie lokal analysiert werden kann, um zu testen, ob eine Erweiterung als leistungsbeeinflussende Erweiterung angezeigt werden kann. Weitere Informationen finden Sie unter [Gewusst wie: Diagnose der Erweiterungsleistung](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Fehlerbehebung bei VSPackages
 Finden Sie heraus, welche Techniken zur Fehlerbehebung von VSPackages, die nicht geladen werden oder Fehler aufweisen, gefunden werden: [Problembehandlung vsPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
