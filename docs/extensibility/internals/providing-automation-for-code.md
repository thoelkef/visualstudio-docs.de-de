---
title: Bereitstellen von Automatisierung für Code | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705996"
---
# <a name="providing-automation-for-code"></a>Bereitstellen von Automatisierung für Code
Das Erstellen eines Automatisierungsmodells für Ihren Code ist nicht erforderlich. Das Environment SDK stellt dafür kein Beispiel bereit. Informationen zu Codemodellen finden <xref:EnvDTE.CodeModel> Sie im Objekt.

 Um ein Codemodell zu implementieren, müssen Sie alle Schnittstellen implementieren, die von Ihrer internen Datenstruktur bestimmt werden. Die Objekte müssen von `IDispatch` der Klasse abgeleitet werden.

 Die Objekte, die <xref:EnvDTE.CodeModel> <xref:EnvDTE.FileCodeModel>Sie erweitern und <xref:EnvDTE.Project> , sind im Objekt verfügbar und sehen wie folgt aus:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Sie können wählen, `CodeModel` ob `FileCodeModel` Sie nur die oder `Project` die <xref:EnvDTE.ProjectItem> Schnittstelle in dem Objekt implementieren möchten, das Sie von Ihrem und Ihren Objekten zurückgeben. Stellen Sie alle Funktionen dieser Schnittstelle bereit, die für Ihr Projektsystem geeignet sind.

 Wenn Sie Features hinzufügen möchten, z. B. Methoden oder `CodeModel` `FileCodeModel` Eigenschaften, die nicht über den Standard und Schnittstellen verfügbar sind, erstellen Sie eine eigene Schnittstelle, die vom Standard erbt. Dokumentieren Sie dies mit Ihrem Projektsystem, damit die Endbenutzer wissen, dass sie danach suchen. Sie geben die Standardschnittstelle zurück, `QueryInterface` aber der Benutzer kann die Methode aufrufen oder auf die Schnittstelle umwerfen, wenn bekannt ist, dass sie vorhanden ist.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)
