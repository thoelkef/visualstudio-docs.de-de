---
title: Erstellen von apps mit nativer Benutzeroberfläche mithilfe von xamarin
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 33
ms.author: crdun
manager: crdun
ms.openlocfilehash: 204d3ee68aace07ed19e5913309a122d6d775a0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918343"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Erstellen von Apps mit nativer Benutzeroberfläche über Xamarin in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem Sie die Schritte unter [Setup und Installation](../cross-platform/setup-and-install.md) und [Überprüfen Ihrer Xamarin-Umgebung](../cross-platform/verify-your-xamarin-environment.md) ausgeführt haben, zeigt Ihnen diese exemplarische Vorgehensweise das Erstellen einer einfachen (unten gezeigten) Xamarin-App mit nativen Benutzeroberflächenebenen. Bei nativen Benutzeroberflächen befindet sich der freigegebene Code in einer portablen Klassenbibliothek (PCL), und die einzelnen Plattformprojekte enthalten die UI-Definitionen.

 ![Xamarin-App unter Android und Windows Phone](../cross-platform/media/cross-plat-xamarin-build-1.png "Plattformübergreifendes xamarin-Build 1")

 Zum Erstellen müssen Sie die folgenden Schritte ausführen:

- [Einrichten der Lösung](#solution)

- [Schreiben von freigegebenem Datendienstcode](#dataservice)

- [Entwickeln der Benutzeroberfläche für Android](#Android)

- [Entwickeln der Benutzeroberfläche für Windows Phone](#Windows)

- [Nächste Schritte](#next)

> [!TIP]
> Den vollständigen Quellcode für dieses Projekt finden Sie im [Repository „Mobile Samples“ auf GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Wenn Sie Probleme haben oder Fehler auftreten, posten Sie Ihre Fragen bitte auf [forums.xamarin.com](https://forums.xamarin.com/). Viele Fehler können behoben werden, indem ein Update auf die neuesten von Xamarin erforderlichen SDKs durchgeführt wird. Diese werden unter [Xamarin Release Notes (Xamarin-Versionshinweise)](https://developer.xamarin.com/) für die einzelnen Plattformen beschrieben.
>
> [!NOTE]
> Die Xamarin-Entwicklerdokumentation bietet außerdem, wie nachstehend aufgelistet, eine Reihe von exemplarischen Vorgehensweisen mit Schnellstart- und vertiefenden Abschnitten. Achten Sie für jede dieser Seiten darauf, dass „Visual Studio“ oben rechts auf der Seite ausgewählt ist, damit Visual Studio-spezifische exemplarische Vorgehensweisen angezeigt werden.
>
> - Xamarin-Apps mit systemeigener Benutzeroberfläche:
>
>   - [Hello, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (einfache App mit einem Bildschirm)
>   - [Hello, Android multiscreen](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (App mit Navigation zwischen Bildschirmen)
>   - [Android Fragments Walkthrough](/xamarin/android/platform/fragments/implementing-with-fragments/) (u. a. für die Demonstration von Haupt-/Detailbildschirmen verwendet)
>   - [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
>   - [Hello, iOS Multiscreen](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)
>   - Xamarin-Apps mit Xamarin.Forms (gemeinsame Benutzeroberfläche)
>
>   - [Hello, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)
>   - [Hello, Xamarin.Forms Multiscreen](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)

## <a name="set-up-your-solution"></a><a name="solution"></a> Einrichten Ihrer Projektmappe
 Mit diesen Schritten erstellen Sie eine Xamarin-Projektmappe mit nativer Benutzeroberfläche, die eine PCL für freigegebenen Code und zwei zusätzliche NuGet-Pakete enthält.

1. Erstellen Sie in Visual Studio eine neue Projektmappe **Leere App (Native Portable)**, und nennen Sie diese **WeatherApp**. Sie finden diese Vorlage am einfachsten, indem Sie **Native Portable** in das Suchfeld eingeben.

    Wenn dies nicht der Fall ist, müssen Sie möglicherweise xamarin installieren oder das Visual Studio 2015-Feature aktivieren. Weitere Informationen finden Sie unter [Setup und Installation](../cross-platform/setup-and-install.md).

2. Nachdem Sie auf „OK“ geklickt haben, um die Projektmappe zu erstellen, verfügen Sie über eine Reihe einzelner Projekte:

   - **WeatherApp (Portable)**: die PCL, in die Sie Code schreiben, der plattformübergreifend freigegeben wird, einschließlich allgemeiner Geschäftslogik und UI-Code, die mit Xamarin.Forms verwendet werden.

   - **WeatherApp.Droid**: das Projekt, das den systemeigenen Android-Code enthält. Dieses wird als Standardstartprojekt festgelegt.

   - **WeatherApp.iOS**: das Projekt, das den systemeigenen iOS-Code enthält.

   - **WeatherApp.WinPhone (Windows Phone 8.1)**: das Projekt, das den nativen Phone-Code enthält.

     Innerhalb eines jeden nativen Projekts haben Sie Zugriff auf den nativen Designer für die entsprechende Plattform und können so plattformspezifische Bildschirme implementieren.

3. Fügen Sie das NuGet-Paket **Newtonsoft.Json** zum PCL-Projekt hinzu, das Sie zum Verarbeiten der von einem Wetterdatendienst abgerufenen Informationen verwenden:

   - Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf **Projekt 'WeatherApp'**, und wählen Sie **NuGet-Pakete für Projektmappe verwalten...** aus.

        Wählen Sie im NuGet-Fenster die Registerkarte **Durchsuchen** aus, und suchen Sie nach **Newtonsoft**.

   - Wählen Sie **Newtonsoft.Json**aus.

   - Aktivieren Sie auf der rechten Seite des Fensters das Projekt **WeatherApp** (das einzige Projekt, in dem Sie das Paket installieren müssen).

   - Stellen Sie sicher, dass das **Version** -Feld auf die **neueste stabile** Version festgelegt ist.

   - Klicken Sie auf **Installieren**.

   - ![Suchen und Installieren des Newtonsoft.Jsfür das nuget-Paket](../cross-platform/media/crossplat-xamarin-formsguide-5.png "Crossplat xamarin formsguide 5")

4. Wiederholen Sie Schritt 3, um das **Microsoft.Net.Http**-Paket zu suchen und zu installieren.

5. Erstellen Sie die Projektmappe, und vergewissern Sie sich, dass keine Buildfehler aufgetreten sind.

## <a name="write-shared-data-service-code"></a><a name="dataservice"></a> Schreiben von frei gegebenem Datendienst Code
 Im Projekt **weatherapp (Portable)** schreiben Sie Code für die portable Klassenbibliothek (Portable Class Library, PCL), die auf allen Plattformen gemeinsam genutzt wird. In App-Paketen, die von iOS-, Android- und Windows Phone-Projekten erstellt werden, ist die PCL automatisch enthalten.

 Mit den folgenden Schritten fügen Sie nun Code zu der PCL hinzu, um auf Daten dieses Wetterdiensts zuzugreifen und diese zu speichern:

1. Um dieses Beispiel ausführen zu können, müssen Sie sich zuerst für einen kostenlosen API-Schlüssel unter Anmelden [http://openweathermap.org/appid](https://openweathermap.org/appid) .

2. Klicken Sie mit der rechten Maustaste auf das **WeatherApp**-Projekt, und wählen Sie **Hinzufügen > Klasse…** aus. Geben Sie der Datei im Dialogfeld **Neues Element hinzufügen** den Namen **Weather.cs**. Sie nutzen diese Klasse später, um Daten aus dem Wetterdatendienst zu speichern.

3. Ersetzen Sie den gesamten Inhalt von **Weather.cs** durch folgenden Code:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

4. Fügen Sie eine weitere Klasse zum PCL-Projekt namens **DataService.cs** hinzu, die Sie zum Verarbeiten von JSON-Daten aus dem Wetterdatendienst verwenden.

5. Ersetzen Sie den gesamten Inhalt von **DataService.cs** durch folgenden Code:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

6. Fügen Sie der PCL eine dritte Klasse hinzu, und nennen Sie diese **Core** . Darin wird die freigegebene Geschäftslogik abgelegt, z.B. Logik, die mithilfe einer Postleitzahl eine Abfragezeichenfolge bildet, den Wetterdatendienst aufruft und anschließend eine Instanz der **Weather** -Klasse auffüllt.

7. Ersetzen Sie den Inhalt von **Core.cs** durch folgenden Code:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

8. Ersetzen Sie *YOUR KEY HERE* im Code durch den API-Schlüssel, den Sie in Schritt 1 erhalten haben. (Sie müssen ihn noch in Anführungszeichen setzen.)

9. Löschen Sie MyClass.cs in der PCL, da wir ihn nicht verwenden werden.

10. Erstellen Sie das PCL-Projekt **WeatherApp** , um sicherzustellen, dass der Code korrekt ist.

## <a name="design-ui-for-android"></a><a name="Android"></a> Entwerfen der Benutzeroberfläche für Android
 Wir entwickeln nun die Benutzeroberfläche, verbinden diese mit dem freigegebenen Code und führen dann die App aus.

### <a name="design-the-look-and-feel-of-your-app"></a>Entwickeln des Erscheinungsbilds und Verhaltens der App

1. Erweitern Sie im **Projektmappen-Explorer** den Ordner **WeatherApp.Droid**>**Ressourcen**>**Layout**, und öffnen Sie **Main.axml**. Dadurch wird die Datei im visuellen Designer geöffnet. (Wenn ein Java-bezogener Fehler angezeigt wird, lesen Sie diesen [Blogbeitrag](https://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    > Es sind viele weitere Dateien in diesem Projekt vorhanden. Sie alle zu besprechen, würde den Rahmen dieses Themas sprengen. Wenn Sie jedoch mehr über die Struktur eines Android-Projekts erfahren möchten, finden Sie ausführliche Informationen unter [Part 2 Deep Dive (Detailinformationen, Teil 2, in englischer Sprache)](/xamarin/android/get-started/hello-android/hello-android-deepdive?pivots=windows) des Themas „Hello Android“ auf xamarin.com.

2. Markieren und löschen Sie die Standardschaltfläche, die im Designer angezeigt wird.

3. Öffnen Sie die Toolbox mit **Ansicht > Andere Fenster > Toolbox**.

4. Ziehen Sie aus dem **Werkzeugkasten**ein **RelativeLayout** -Steuerelement in den Designer. Sie werden dieses Steuerelement als übergeordneten Container für andere Steuerelemente verwenden.

    > [!TIP]
    > Wenn das Layout zu einem beliebigen Zeitpunkt noch nicht richtig angezeigt zu werden scheint, speichern Sie die Datei. Wechseln Sie dann zwischen den Registerkarten **Design** und **Quelle**, um eine Aktualisierung durchzuführen.

5. Setzen Sie im Fenster **Eigenschaften** die Eigenschaft **Hintergrund** (in der Formatvorlagengruppe) auf `#545454`.

6. Ziehen Sie aus dem **Werkzeugkasten**ein **TextView** -Steuerelement auf das **RelativeLayout** -Steuerelement.

7. Legen Sie im Fenster **Eigenschaften** die folgenden Eigenschaften fest. (Hinweis: Es kann helfen, die Liste mithilfe der Sortierschaltfläche in der Symbolleiste des Fensters „Eigenschaften“ alphabetisch zu sortieren):

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**text**|**Search by Zip Code**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginLeft**|`10dp`|
    |**TextColor**|`@android:color/white`|
    |**textStyle**|`bold`|

    > [!TIP]
    > Beachten Sie, dass viele Eigenschaften nicht über eine Dropdownliste mit Werten verfügen, die Sie auswählen können.  Es kann schwierig sein, zu raten, welcher Zeichenfolgenwert für eine bestimmte Eigenschaft verwendet werden soll. Vorschläge können Sie möglicherweise erhalten, indem Sie auf der Seite der Klasse [R.attr](https://developer.android.com/reference/android/R.attr.html) nach dem Namen einer Eigenschaft suchen.
    >
    >  Eine schnelle Websuche führt außerdem häufig zu einer Seite, auf [http://stackoverflow.com/](https://stackoverflow.com/) der andere die gleiche Eigenschaft verwendet haben.

     Wenn Sie zur Ansicht **Quelle** wechseln, sollten Sie den folgenden Code für dieses Element als Referenz sehen:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_centerVertical="true"
        android:layout_marginLeft="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

8. Ziehen Sie aus der **Toolbox** ein **TextView**-Steuerelement auf das Steuerelement **RelativeLayout**, und positionieren Sie es unter dem Steuerelement „ZipCodeSearchLabel“. Sie können dazu das neue Steuerelement auf dem entsprechenden Rand des vorhandenen Steuerelements ablegen. Es ist hilfreich, den Designer hierzu etwas zu vergrößern.

9. Legen Sie im **Eigenschaftsfenster** diese Eigenschaften fest:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**text**|**PLZ**|
    |**id**|`@+id/ZipCodeLabel`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginTop**|`5dp`|

     Der Code in der Ansicht **Quelle** sollte wie folgt aussehen:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginTop="5dp"
        android:layout_marginLeft="10dp" />
    ```

10. Ziehen Sie aus der **Toolbox** ein **Number**-Steuerelement auf **RelativeLayout**, und positionieren Sie es unter der Beschriftung **Zip Code**. Legen Sie dann die folgenden Eigenschaften fest:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**width**|`165dp`|

     Hier wieder der Code:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginLeft="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp" />
    ```

11. Ziehen Sie aus der **Toolbox** eine **Schaltfläche** auf das Steuerelement **RelativeLayout**, und positionieren Sie sie rechts neben dem Steuerelement „zipCodeEntry“. Legen Sie dann diese Eigenschaften fest:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**id**|`@+id/weatherBtn`|
    |**text**|**Get Weather**|
    |**layout_marginLeft**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**width**|`165dp`|

    ```xml
    <Button    android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginLeft="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

12. Sie verfügen jetzt über ausreichend Erfahrung, um eine einfache Benutzeroberfläche mit dem Android-Designer zu erstellen. Sie können ferner eine Benutzeroberfläche erstellen, indem Sie Markup direkt zur .asxml-Datei auf der Seite hinzufügen. Um die restliche Benutzeroberfläche auf diese Weise zu erstellen, wechseln Sie zur Ansicht „Quelle“ im Designer. Fügen Sie dann das folgende Markup *unter* dem Tag `</RelativeLayout>` ein. (Richtig, unter dem Tag – diese Elemente sind nicht in ReleativeLayout enthalten.)

    ```xml
    <TextView
            android:text="Location"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationLabel"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationText"
            android:layout_marginLeft="20dp"
            android:layout_marginBottom="10dp" />
        <TextView
            android:text="Temperature"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Wind Speed"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Humidity"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidtyLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Visibility"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunrise"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunset"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />

    ```

13. Speichern Sie die Datei, und wechseln Sie zur Ansicht **Design**. Die Benutzeroberfläche sollte folgendermaßen aussehen:

     ![Benutzeroberfläche für Android-App](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")

14. Öffnen Sie **MainActivity.cs**, und löschen Sie die Zeilen in der *OnCreate*-Methode, die auf die zuvor entfernte Standardschaltfläche verweisen. Wenn Sie fertig sind, sollte der Code folgendermaßen aussehen:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

15. Erstellen Sie das Android-Projekt, um Ihre Arbeit zu überprüfen. Hinweis: Beim Erstellen werden Steuerelement-IDs zur Datei **Resource.Designer.cs** hinzugefügt, sodass Sie im Code mit Namen auf die Steuerelemente verweisen können.

### <a name="consume-your-shared-code"></a>Verwenden des freigegebenen Codes

1. Öffnen Sie die Datei **MainActivity.cs** des Projekts **WeatherApp** im Code-Editor, und ersetzen Sie seinen Inhalt durch den unten stehenden Code. Dieser Code ruft die `GetWeather` -Methode auf, die Sie im freigegebenen Code definiert haben. Dann werden auf der Benutzeroberfläche der App die Daten angezeigt, die durch diese Methode abgerufen werden.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App", MainLauncher = true, Icon = "@drawable/icon")]
        public class MainActivity : Activity
        {
            protected override void OnCreate(Bundle bundle)
            {
                base.OnCreate(bundle);

                SetContentView(Resource.Layout.Main);

                Button button = FindViewById<Button>(Resource.Id.weatherBtn);

                button.Click += Button_Click;
            }

            private async void Button_Click(object sender, EventArgs e)
            {
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);

                if (!String.IsNullOrEmpty(zipCodeEntry.Text))
                {
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;
                }
            }
        }
    }
    ```

### <a name="run-the-app-and-see-how-it-looks"></a>Ausführen der App und Prüfen der Anzeige

1. Stellen Sie im **Projektmappen-Explorer** sicher, dass das Projekt **WeatherApp.Droid** als Startprojekt festgelegt ist.

2. Wählen Sie ein geeignetes Gerät oder Emulatorziel, und starten Sie die App durch Drücken der Taste F5.

3. Geben Sie auf dem Gerät oder im Emulator eine gültige Postleitzahl für die USA in das Bearbeitungsfeld ein (zum Beispiel: 60601), und drücken Sie dann **Get Weather**. In den Steuerelementen werden nun Wetterdaten für diese Region angezeigt.

     ![Wetter-App für Android und Windows Phone](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")

> [!TIP]
> Den vollständigen Quellcode für dieses Projekt finden Sie im [Repository „mobile-samples“ auf GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="design-ui-for-windows-phone"></a><a name="Windows"></a> Entwerfen der Benutzeroberfläche für Windows Phone
 Wir entwickeln nun die Benutzeroberfläche für Windows Phone, verbinden sie mit Ihrem freigegebenen Code und führen dann die App aus.

### <a name="design-the-look-and-feel-of-your-app"></a>Entwickeln des Erscheinungsbilds und Verhaltens der App
 Das Entwickeln einer nativen Windows Phone-Benutzeroberfläche in einer Xamarin-App unterscheidet sich nicht von anderen nativen Windows Phone-Apps. Daher wird hier nicht ausführlich auf die Verwendung des Designers eingegangen. Entsprechende Informationen finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer in Visual Studio](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 Öffnen Sie stattdessen einfach „MainPage.xaml“, und ersetzen Sie den gesamten XAML-Code durch den folgenden Code:

```xaml
<Page
    x:Class="WeatherApp.WinPhone.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.WinPhone"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <Grid>
        <StackPanel HorizontalAlignment="Left" Height="40" Margin="10,0,0,0" VerticalAlignment="Top" Width="400">
            <TextBlock x:Name="pageTitle" Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="10,40,0,0" VerticalAlignment="Top" Width="400" Background="#FF545454">

            <TextBlock x:Name="zipCodeSearchLabel" TextWrapping="Wrap" Text="Search by Zip Code" FontSize="18" FontWeight="Bold" HorizontalAlignment="Left" Margin="10,10,0,0"/>
            <TextBlock x:Name="zipCodeLabel" TextWrapping="Wrap" Text="Zip Code" Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            <StackPanel Orientation="Horizontal">
                <TextBox x:Name="zipCodeEntry" Margin="10,10,0,0" Text="" VerticalAlignment="Top" InputScope="Number" Width="165" />
                <Button x:Name="weatherBtn" Content="Get Weather" Width="165" Margin="20,0,0,0" Height="60" Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        <StackPanel Margin="10,175,0,0">
            <TextBlock x:Name="locationLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Location" VerticalAlignment="Top"/>
            <TextBlock x:Name="locationText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="windLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Wind Speed" VerticalAlignment="Top"/>
            <TextBlock x:Name="windText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Humidity" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunriweatherse" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunset" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
        </StackPanel>
    </Grid>
</Page>
```

 Die Benutzeroberfläche sollte in der Entwurfsansicht folgendermaßen aussehen:

 ![Windows Phone-App-Benutzeroberfläche](../cross-platform/media/xamarin-winphone-finalui.png "Xamarin_WinPhone_FinalUI")

### <a name="consume-your-shared-code"></a>Verwenden des freigegebenen Codes

1. Wählen Sie im Designer die Schaltfläche **Get Weather** .

2. Wählen Sie im Fenster **Eigenschaften** die Schaltfläche Ereignishandler (![Symbol für Visual Studio-Ereignis](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")Handler) aus.

     Dieses Symbol wird in der oberen Ecke des **Eigenschaftsfensters** angezeigt.

3. Geben Sie neben dem **Click** -Ereignis **GetWeatherButton_Click**ein, und drücken Sie dann die Eingabetaste.

     Dadurch wird ein Ereignishandler mit dem Namen `GetWeatherButton_Click`erstellt. Der Code-Editor wird geöffnet, und der Cursor wird innerhalb des Codeblocks des Ereignishandlers platziert.  Hinweis: Wenn der Editor nicht geöffnet wird, wenn Sie die EINGABETASTE drücken, doppelklicken Sie einfach auf den Ereignisnamen.

4. Ersetzen Sie diesen Ereignishandler durch den folgenden Code.

    ```csharp
    private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            locationText.Text = weather.Title;
            tempText.Text = weather.Temperature;
            windText.Text = weather.Wind;
            visibilityText.Text = weather.Visibility;
            humidityText.Text = weather.Humidity;
            sunriseText.Text = weather.Sunrise;
            sunsetText.Text = weather.Sunset;

            weatherBtn.Content = "Search Again";
        }
    }
    ```

     Dieser Code ruft die `GetWeather` -Methode auf, die Sie im freigegebenen Code definiert haben. Es handelt sich um die gleiche Methode, die Sie in der Android-App aufgerufen haben. Dieser Code zeigt ebenfalls Daten, die mit dieser Methode aus den Steuerelementen der Benutzeroberfläche der App gewonnen wurden.

5. Löschen Sie in "MainPage.Xaml.cs", das geöffnet ist, den gesamten Code in der Methode **OnNavigatedTo**. Dieser Code betraf lediglich die Standardschaltfläche, die entfernt wurde, als wir den Inhalt von „MainPage.xaml“ ersetzt haben.

### <a name="run-the-app-and-see-how-it-looks"></a>Ausführen der App und Prüfen der Anzeige

1. Legen Sie im **Projektmappen-Explorer** das Projekt **WeatherApp.WinPhone** als Startprojekt fest.

2. Starten Sie die App durch Drücken der Taste "F5".

3. Geben Sie im Windows Phone-Emulator eine gültige Postleitzahl für die USA in das Bearbeitungsfeld ein (zum Beispiel: 60601), und drücken Sie **Get Weather**. In den Steuerelementen werden nun Wetterdaten für diese Region angezeigt.

     ![Windows-Version der ausgeführten App](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")

> [!TIP]
> Den vollständigen Quellcode für dieses Projekt finden Sie im [Repository „mobile-samples“ auf GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="next-steps"></a><a name="next"></a> Nächste Schritte
 **Hinzufügen einer Benutzeroberfläche für iOS zum Projekt**

 Erweitern Sie dieses Beispiel, indem Sie eine native Benutzeroberfläche für iOS hinzufügen. Hierzu müssen Sie über Ihr lokales Netzwerk eine Verbindung zu einem Mac herstellen, auf dem Xcode und Xamarin installiert sind. Anschließend können Sie den iOS-Designer direkt in Visual Studio verwenden. Weitere Informationen finden Sie im [Repository „mobile-samples“ auf GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

 Beachten Sie auch die exemplarische Vorgehensweise für [Hello, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?pivots=windows) (xamarin.com). Hinweis: Achten Sie darauf, dass auf „xamarin.com“ oben rechts auf jeder Seite „Visual Studio“ ausgewählt ist, damit der richtige Satz von Anweisungen angezeigt wird.

 **Hinzufügen von plattformspezifischem Code in einem freigegebenen Projekt**

 Freigegebener Code in einer PCL ist plattformneutral, da die PCL einmal kompiliert und in alle plattformspezifischen App-Pakete aufgenommen wird. Wenn Sie freigegebenen Code schreiben möchten, der eine bedingte Kompilierung verwendet, um plattformspezifischen Code zu isolieren, können Sie ein *freigegebenes* Projekt verwenden. Weitere Informationen finden Sie unter [Code Sharing Options (Codefreigabeoptionen)](/xamarin/cross-platform/app-fundamentals/code-sharing) (xamarin.com).

## <a name="see-also"></a>Weitere Informationen
 [Xamarin-Entwickler Website](/xamarin/) [Windows dev Center](https://dev.windows.com/en-us) [SWIFT und c# kurz Referenz Poster](https://aka.ms/scposter)
