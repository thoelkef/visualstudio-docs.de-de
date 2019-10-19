---
title: Arbeiten mit Texturen und Bildern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 93813aa734c615e7f045c98c776e600be4ee3fab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663934"
---
# <a name="working-with-textures-and-images"></a>Arbeiten mit Texturen und Bildern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Bildbearbeitung in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zum Erstellen und Bearbeiten von Texturen und Bildern verwenden. Die Bildverarbeitung unterstützt aufwändige Textur- und Bildformate, wie solche, die in der Entwicklung von DirectX-Apps zum Einsatz kommen.

> [!NOTE]
> Die Bildverarbeitung unterstützt keine Bilder mit geringer Farbtiefe, wie Symbole oder Cursor. Zum Erstellen oder Ändern dieses Typs Bilder können Sie den [Image Editor for Icons](https://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd)verwenden.

## <a name="textures-and-images"></a>Texturen und Bilder
 Texturen und Bilder sind, grundlegend betrachtet, nur Tabellen von Daten, die dazu dienen, visuelle Details in Apps mit grafischer Benutzeroberfläche bereitzustellen. Die Art von Detail, die von einer Textur oder einem Bild bereitgestellt wird, hängt vom Einsatzzweck ab, aber Farbmuster, Alphawerte (Transparenz), Oberflächennormale und Höhenwerte stellen gängige Beispiele dar. Der wichtigste Unterschied zwischen einer Textur und einem Bild besteht darin, dass eine Textur für die Verwendung in Kombination mit der Darstellung einer Form bestimmt ist – normalerweise einem 3D-Modell –, um ein vollständiges Objekt oder eine Szene darzustellen, während ein Bild normalerweise eine eigenständige Darstellung des Objekts oder der Szene ist.

 Häufig verwendete Texturarten sind z. B.:

 Textur Karten Textur Maps enthalten Farbwerte, die als eine zwei-, zwei-oder dreidimensionale Matrix organisiert sind. Sie werden verwendet, um Farbdetails auf dem betroffenen Objekt bereitzustellen. Farben werden häufig mithilfe der Farbkanäle RGB (Rot, Grün, Blau) codiert und können einen vierten Kanal, Alpha, zur Darstellung der Transparenz beinhalten. Weniger üblich, aber möglich, ist die Codierung von Farben in einem anderen Farbschema oder die Darstellung von anderen Informationen als Alpha im vierten Kanal – etwa der Höhe.

 Normale Karten normale Zuordnungen enthalten Oberflächen normale. Sie werden verwendet, um Beleuchtungsdetails für das betroffene Objekt bereitzustellen. Normale werden üblicherweise codiert, indem die roten, grünen und blauen Farbkomponenten zum Speichern der X-, Y- und Z-Dimensionen für den Vektor verwendet werden. Es gibt jedoch auch andere Codierungen – beispielsweise Codierungen auf der Grundlage von Polkoordinaten.

 Height Maps Height Maps enthalten Höhen Felddaten. Sie werden verwendet, um einen Typ von geometrischem Detail auf dem betroffenen Objekt – mithilfe von Shadercode zum Berechnen des gewünschten Effekts – oder Datenpunkte für Einsatzzwecke wie die Geländegenerierung bereitzustellen . Höhenwerte werden normalerweise durch Nutzung eines Kanals in einer Textur codiert.

 Cubemaps-Cubemaps können unterschiedliche Arten von Daten enthalten – z. b. Farben oder normale –, sind aber in Form von sechs Texturen auf den Flächen eines Cubes angeordnet. Daher werden Cubemaps nicht durch die Angabe von Texturkoordinaten sondern durch Angabe eines Vektors dargestellt, dessen Ursprung das Zentrum des Würfels ist. Das Sample wird am Schnittpunkt des Vektors mit dem Würfel erfasst. Mithilfe von Cubemaps kann eine Näherung der Umgebung bereitgestellt werden, die zum Berechnen von Reflexionen dienen kann – das wird als *Environment Mapping*bezeichnet – oder um Texturen auf sphärischen Objekten mit geringerer Verzerrung zu darzustellen, als sie mit einfachen, zweidimensionalen Texturen erreicht werden kann.

 Jede Textur kann auf verschiedene Weise codiert und komprimiert werden, die orthogonal zu der Art der in der Textur enthaltenen Daten oder ihrer Dimensionalität oder „Form“ ist. Allerdings ergeben verschiedene Codierungs- und Komprimierungsverfahren für verschiedene Arten von Daten unterschiedlich gute Ergebnisse.

 Sie können die Bildbearbeitung verwenden, um Texturen und Bilder auf ähnliche Weise wie in anderen Bild-Editoren zu erstellen und zu bearbeiten. Die Bildbearbeitung bietet außerdem MipMaps und weitere Features für die Verwendung in der 3D-Grafik und unterstützt viele der stark komprimierten Texturformate mit Hardwarebeschleunigung, die von DirectX unterstützt werden.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Image Editor](../designers/image-editor.md)|Beschreibt die Verwendung der Bildbearbeitung für die Arbeit mit Texturen und Bildern.|
|[Beispiele für die Bildbearbeitung](../designers/image-editor-examples.md)|Enthält Links zu Themen, in denen die Verwendung der Bildbearbeitung für das Ausführen häufiger Aufgaben der Bildverarbeitung veranschaulicht wird.|
