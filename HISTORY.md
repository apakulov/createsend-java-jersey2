# createsend-java history

## v3.0.0 - Whenever this is released

* Added support for authenticating using OAuth. See the [README](README.md#authenticating) for full usage instructions.
* Refactored authentication so that it is _always_ done at the instance level. This introduces some breaking changes, which are clearly explained below.
  * Authentication using an API key is no longer supported using the `config.properties` or `createsend.properties` files.
  
      So if you _previously_ entered your API key into a properties file as follows:
      
      ```
      createsend.apikey = your api key
      ```

      If you want to authenticate with an API key, you should _now_ always authenticate at the instance level. For example, as follows:

      ```java
      import com.createsend.Clients;
      import com.createsend.models.campaigns.SentCampaign;
      import com.createsend.util.ApiKeyAuthenticationDetails;
      import com.createsend.util.exceptions.CreateSendException;

      public class Tester {
          public static void main(String[] args) throws CreateSendException {
              ApiKeyAuthenticationDetails auth = new ApiKeyAuthenticationDetails(
                  "your api key");
              Clients clients = new Clients(auth, "your client id");
              SentCampaign[] campaigns = clients.sentCampaigns();
          }
      }
      ```

## v2.6.0 - 4 Jan, 2013  (f8cd13c)

* Added support for instantiating JerseyClientImpl using a specific API key.

## v2.5.0 - 11 Dec, 2012  (5b16f78)

* Added support for including from name, from email, and reply to email in
drafts, scheduled, and sent campaigns.
* Added support for campaign text version urls.
* Added support for transferring credits to/from a client.
* Added support for getting account billing details as well as client credits.
* Made all date fields optional when getting paged results.

## v2.4.0 - 5 Nov, 2012   (4c3cc6a1)

* Added EmailClient class and Campaigns.emailClientUsage().
* Added support for ReadsEmailWith field on subscriber objects.
* Added support for retrieving unconfirmed subscribers for a list.
* Added support for suppressing email addresses.
* Added support for retrieving spam complaints for a campaign, as well as adding SpamComplaints field to campaign summary output.
* Added VisibleInPreferenceCenter field to custom field output.
* Added support for setting preference center visibility when creating custom
fields.
* Added the ability to update a custom field name and preference visibility.
* Added documentation explaining that TextUrl may be provided as null or as an
empty string when creating a campaign.

## v2.3.0 - 10 Oct, 2012   (2d5178e0)

* Added support for creating campaigns from templates.
* Added support for unsuppressing an email address.

## v2.2.0 - 17 Sep, 2012   (8f9b6c45)

* Added WorldviewURL field to com.createsend.models.campaigns.CampaignSummary.
* Introduced CampaignEventWithGeoData, CampaignOpen, and CampaignClick to
support correct retrieval of open and click data.

## v2.1.0 - 30 Aug, 2012   (67981b4d)

* Added support for basic / unlimited pricing.

## v2.0.0 - 23 Aug, 2012   (97c5d167)

* Removed com.createsend.Clients.setAccess() and removed all other parts of the
library which were allowing calls to the API in a deprecated manner.

## v1.2.0 - 22 Aug, 2012   (ef867e9b)

* Added support for UnsubscribeSetting field when creating, updating and
getting list details.
* Added support for AddUnsubscribesToSuppList and ScrubActiveWithSuppList
fields when updating a list.
* Added com.createsend.Clients.listsForEmailAddress() to support finding all
client lists to which a subscriber with a specific email address belongs.

## v1.1.1 - 23 Jul, 2012   (f777ad8a)

* Added support for specifying whether subscription-based autoresponders should
be restarted when adding or updating subscribers.

## v1.1.0 - 12 Jul, 2012   (2de00dee)

* Added support for team management.
* Added Travis CI support

## 1.0.5 - 31 Oct, 2011   (a9e26af9)

* Added support for new APIs.
* Fixed field names to be consistent with fields returned by API.

## 1.0.4 - 11 Sep, 2011   (98b6c2c9)

* Fixed #3. Removed TemplateScreenshotURL from the sample for creating
a template.

## 1.0.3 - 17 Aug, 2011   (384ed6cc)

* Initial release which supports current Campaign Monitor API.