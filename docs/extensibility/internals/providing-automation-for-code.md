---
title: Bereitstellen von Automatisierung für Code | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724959"
---
# <a name="providing-automation-for-code"></a>Bereitstellen von Automatisierung für Code
Das Erstellen eines Automatisierungs Modells für Ihren Code ist nicht erforderlich. Das Umgebungs-SDK bietet hierfür kein Beispiel. Einen Einblick in Code Modelle finden Sie im <xref:EnvDTE.CodeModel>-Objekt.

 Zum Implementieren eines Code Modells müssen Sie alle Schnittstellen implementieren, die von der internen Datenstruktur bestimmt werden. Die Objekte müssen von der `IDispatch` Klasse abgeleitet werden.

 Die-Objekte, die Sie erweitern, <xref:EnvDTE.CodeModel> und <xref:EnvDTE.FileCodeModel>, sind über das <xref:EnvDTE.Project>-Objekt verfügbar und sehen wie folgt aus:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Sie können auswählen, dass Sie nur die `CodeModel` oder die `FileCodeModel` Schnittstelle in dem Objekt implementieren, das Sie aus dem `Project` und <xref:EnvDTE.ProjectItem> Objekten zurückgeben. Stellen Sie eine beliebige Funktionalität von dieser Schnittstelle bereit, die für Ihr Projekt System geeignet ist.

 Wenn Sie Funktionen hinzufügen möchten, z. b. Methoden oder Eigenschaften, die nicht über die standardmäßigen `CodeModel` und `FileCodeModel` Schnittstellen verfügbar sind, erstellen Sie eine eigene Schnittstelle, die vom Standard erbt. Stellen Sie sicher, dass Sie Sie mit Ihrem Projekt System dokumentieren, damit Endbenutzer darauf achten können. Sie geben die Standardschnittstelle zurück, aber der Benutzer kann die `QueryInterface`-Methode oder eine Umwandlung in die-Schnittstelle durchsetzen, wenn bekannt ist, dass Sie vorhanden ist.

## <a name="see-also"></a>Siehe auch
- [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)