---
title: Source Control-Laufzeitdetails | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705036"
---
# <a name="source-control-runtime-details"></a>Laufzeitdetails für die Quellcodeverwaltung
Ein Projekt wird der Quellcodeverwaltung hinzugefügt, wenn der Benutzer eine Datei im Projekt zur Quellcodeverwaltung oder über einen Automatisierungscontroller, z. B. einen Assistenten, hinzufügt. Ein Projekt gibt nicht selbst an, dass es sich unter Quellcodeverwaltung befindet. Es unterstützt die Quellcodeverwaltung, muss jedoch manuell hinzugefügt werden.

## <a name="registering-with-a-source-control-package"></a>Registrieren bei einem Quellcodeverwaltungspaket
 Wenn eine Datei in Ihrem Projekt zur Quellcodeverwaltung hinzugefügt wird, ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> die Umgebung an, um Ihnen vier undurchsichtige Zeichenfolgen bereitzustellen, die vom Quellcodeverwaltungssystem als Cookies verwendet werden. Speichern Sie diese Zeichenfolgen in Ihrer Projektdatei. Diese Zeichenfolgen sollten beim Start des Projekttyps durch Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>an den Quellcodeverwaltungsstub (die Visual Studio-Komponente, die Quellcodeverwaltungspakete verwaltet) übergeben werden. Dies wiederum lädt das entsprechende Quellcodeverwaltungspaket und leitet `IVsSccManager2::RegisterSccProject`den Aufruf an die Implementierung von weiter.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
