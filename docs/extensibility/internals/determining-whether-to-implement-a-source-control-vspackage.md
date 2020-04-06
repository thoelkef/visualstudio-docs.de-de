---
title: Bestimmen, ob ein Quellcodeverwaltungs-VSPackage implementiert werden soll | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708721"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Bestimmen, ob ein Quellcodeverwaltungs-VSPackage implementiert werden soll
In diesem Abschnitt werden die Auswahlmöglichkeiten von Quellcodeverwaltungs-Plug-Ins und Quellcodeverwaltungs-VSPackages zum Erweitern von Quellcodeverwaltungslösungen erläutert und allgemeine Richtlinien für die Auswahl eines geeigneten Integrationspfads erläutert.

## <a name="small-source-control-solution-with-limited-resources"></a>Kleine Quellcodeverwaltungslösung mit begrenzten Ressourcen
 Wenn Sie über begrenzte Ressourcen verfügen und nicht mit dem Aufwand beim Schreiben eines Quellcodeverwaltungspakets belastet werden können, können Sie Source Control Plug-in-API-basierte Plug-Ins erstellen. So können Sie seite an Seite mit Quellcodeverwaltungspaketen arbeiten und bei Bedarf zwischen Quellcodeverwaltungs-Plug-Ins und Paketen wechseln. Weitere Informationen finden Sie unter [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Große Quellcodeverwaltungslösung mit einem umfangreichen Feature-Set
 Wenn Sie eine Quellcodeverwaltungslösung implementieren möchten, die ein umfangreiches Quellcodeverwaltungsmodell bereitstellt, das mithilfe der Quellcodeverwaltungs-Plug-In-API nicht ausreichend erfasst wird, können Sie ein Quellcodeverwaltungspaket als Integrationspfad betrachten. Dies gilt insbesondere dann, wenn Sie das Quellcodeverwaltungsadapterpaket (das mit Quellcodeverwaltungs-Plug-Ins kommuniziert und eine grundlegende Quellcodeverwaltungs-UI bereitstellt) durch Eine eigene ersetzen möchten, sodass Sie die Quellcodeverwaltungsereignisse auf benutzerdefinierte Weise verarbeiten können. Wenn Sie bereits über eine zufriedenstellende Quellcodeverwaltungsbenutzeroberfläche verfügen und diese Erfahrung in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]beibehalten möchten, können Sie mit der Option für das Quellcodeverwaltungspaket genau das tun. Das Quellcodeverwaltungspaket ist nicht generisch und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ausschließlich für die Verwendung mit IDE konzipiert.

 Wenn Sie eine Quellcodeverwaltungslösung implementieren möchten, die Flexibilität und umfassendere Kontrolle über die Quellcodeverwaltungslogik und -benutzeroberfläche bietet, sollten Sie die Integrationsroute für das Quellcodeverwaltungspaket bevorzugen. Ihre Möglichkeiten:

1. Registrieren Sie Ihr eigenes Quellcodeverwaltungs-VSPackage (siehe [Registrierung und Auswahl](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Ersetzen Sie die standardgesteuerte Benutzeroberflächenbenutzeroberfläche durch Ihre benutzerdefinierte Benutzeroberfläche (siehe [Benutzerdefinierte Benutzeroberfläche](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Geben Sie die zu verwendenden Glyphen an und behandeln Sie die Symboldatendes-Explorer-Glyphenereignisse (siehe [Glyphensteuerelement](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Behandeln von Abfragebearbeitungs- und Abfragespeichernsereignissen (siehe [Abfrage bearbeiten Abfrage speichern](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Weitere Informationen
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
