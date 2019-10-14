# lime-scooter-data-analysis
# reference: https://github.com/ubahnverleih/WoBike/blob/master/Lime.md

## login
```bash
curl --request GET \
  --url 'https://web-production.lime.bike/api/rider/v1/login?phone=%2B821012345678'
```

## sms code
- 로그인 이후 sms 폰으로 6자리의 코드를 받는다.

## token
```bash
curl --request POST \
  --cookie-jar - \
  --url 'https://web-production.lime.bike/api/rider/v1/login' \
  --header 'Content-Type: application/json' \
  --data '{"login_code": "123456", "phone": "+821012345678"}'
```

```bash
{ 
   "token":"eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX3Rva2VuIjoiSzM0WlVPRlFCWDdOMiIsImxvZ2luX2NvdW50IjoyfQ.x6QRERZ9S0KITzHI8wXFhITlXb4cWs_MXttRWX2ZO4o",
   "user":{ 
      "id":"K34ZUOFQBX7N2",
      "type":"users",
      "attributes":{ 
         "token":"K34ZUOFQBX7N2",
         "phone_number":"821064816641",
         "email_address":null,
         "has_verified_email_address":false,
         "name":"Lime Rider",
         "given_name":"Lime",
         "surname":"Rider",
         "default_payment_method":null,
         "referral_code":"RTERXSC",
         "num_trips":0,
         "edu":false,
         "subscription_item_states":[ 

         ],
         "promotion_notification":true,
         "donation_profile":{ 
            "id":"7AIBH7KWDJCLH",
            "type":"donation_profiles",
            "attributes":{ 
               "donation_type":"none",
               "donation_organizations":[ 

               ],
               "total_donation_amount":{ 
                  "currency_code":"USD",
                  "amount":0.0,
                  "amount_str":"0.0",
                  "currency_symbol":"$",
                  "display_string":"$0"
               },
               "total_donation_amount_cents":null,
               "currency":null
            }
         },
         "juicer_profile_status":null,
         "juicer_profile_initial_activated_at":null,
         "pod_vehicle_banner_status":"lime_pod_submit_docs",
         "juicer_referral_type":null,
         "accepted_user_agreement_version":2,
         "accepted_compliance_version":1,
         "new_juicer_earnings_amount":{ 
            "currency_code":"USD",
            "amount":150.0,
            "amount_str":"150.0",
            "currency_symbol":"$",
            "display_string":"$150"
         },
         "juicer_referral_amount":null,
         "balance":{ 
            "currency_code":"KRW",
            "amount":0.0,
            "amount_str":"0.0",
            "currency_symbol":"₩",
            "display_string":"₩0"
         },
         "pending_balance":{ 
            "currency_code":"USD",
            "amount":0.0,
            "amount_str":"0.0",
            "currency_symbol":"$",
            "display_string":"$0"
         },
         "new_juicer_earnings_promo_amount":"150",
         "new_juicer_earnings_promo_amount_cents":15000,
         "new_juicer_earnings_promo_amount_cent":15000,
         "new_juicer_earnings_promo_currency":"KRW",
         "juicer_referral_amount_cents":null,
         "juicer_referral_currency":null,
         "balance_cents":0,
         "pending_balance_cents":0,
         "currency":"USD",
         "show_group_ride":false,
         "id_verification_pending":false
      }
   },
   "meta":{ 
      "latest_user_agreement_version":"-1",
      "min_ios_version":"2.11.0",
      "min_android_code":93,
      "flags":"IOS_VERSION_V1.0,ANDROID_VERSION_V1.0",
      "groups":{ 
         "require_email_after_signup":false
      }
   }
}
```
### Cookie
```bash
#HttpOnly_.lime.bike	TRUE	/	TRUE	1602585117	__cfduid	d8e4bf147ebc6507f4c3204742631e9b51571049117
#HttpOnly_web-production.lime.bike	FALSE	/	TRUE	1571049127	_mkra_stck	mysql%3A1571049122.1814234
#HttpOnly_web-production.lime.bike	FALSE	/	TRUE	0	_limebike-web_session	Z2RnYWZlUi9Ybzd1cUpBRC9UcnBaelFsVjV5aE9MYnV4QldLL1p0ZzNKNmxQL3A1dTRLb3hXUXBmMzlzM2NQU3FmVXI2M1BWQmlEb1VWTm1yWmRaYkVsTVZ3Yjg2MnB1dXh3QWp5TDRYb1puL0ZrQmg2TDFzbThabUZoYUFQNlNHbHN6Y2l1bVR0YXZOSmFvalVDWHI4SFk1dVpUbVY5TDVmb3BvUGR3L3ZBbndNcXQzV2htQi9rUHBWODFDV2VTZnk5OG5peHFMclhkVVlUeTBXajRxT05aYnBWckFTcGxZZ1haeWtOcW9zNHhLY3FjYUhnTk1xL09CU0tBOGJmRkF3WWpHU1FmZTdlSCtEQlM4VlQ4T0l3RVZ5UWJma1lQY0V5cDRBN1YwMXkyZEhOSy9TU0RSdUZiYUlrYTdkdWh5aVNlL211V3hMbmszMk90bEQwZ3RnPT0tLUF4N3dzRG9xT0xXZnZreVlOR1NaL3c9PQ%3D%3D--21a30cf41170d4da4501b4cf0382ae53d8ee1ba7
```

## Get bicycles by lat/lng

### sample
```bash
curl --request GET \
  --url 'https://web-production.lime.bike/api/rider/v1/views/map?ne_lat=52.6&ne_lng=13.5&sw_lat=52.4&sw_lng=13.3&user_latitude=52.5311&user_longitude=13.3849&zoom=16' \
  --header 'authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX3Rva2VuIjoiSzM0WlVPRlFCWDdOMiIsImxvZ2luX2NvdW50IjoyfQ.x6QRERZ9S0KITzHI8wXFhITlXb4cWs_MXttRWX2ZO4o' \
  --cookie '_limebike-web_session=Z2RnYWZlUi9Ybzd1cUpBRC9UcnBaelFsVjV5aE9MYnV4QldLL1p0ZzNKNmxQL3A1dTRLb3hXUXBmMzlzM2NQU3FmVXI2M1BWQmlEb1VWTm1yWmRaYkVsTVZ3Yjg2MnB1dXh3QWp5TDRYb1puL0ZrQmg2TDFzbThabUZoYUFQNlNHbHN6Y2l1bVR0YXZOSmFvalVDWHI4SFk1dVpUbVY5TDVmb3BvUGR3L3ZBbndNcXQzV2htQi9rUHBWODFDV2VTZnk5OG5peHFMclhkVVlUeTBXajRxT05aYnBWckFTcGxZZ1haeWtOcW9zNHhLY3FjYUhnTk1xL09CU0tBOGJmRkF3WWpHU1FmZTdlSCtEQlM4VlQ4T0l3RVZ5UWJma1lQY0V5cDRBN1YwMXkyZEhOSy9TU0RSdUZiYUlrYTdkdWh5aVNlL211V3hMbmszMk90bEQwZ3RnPT0tLUF4N3dzRG9xT0xXZnZreVlOR1NaL3c9PQ%3D%3D--21a30cf41170d4da4501b4cf0382ae53d8ee1ba7'
```
### seoul

```bash
curl --request GET \
  --url 'https://web-production.lime.bike/api/rider/v1/views/map?ne_lat=37.5&ne_lng=127.1&sw_lat=37.4&sw_lng=127.0&user_latitude=37.5172&user_longitude=127.0473&zoom=16' \
  --header 'authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX3Rva2VuIjoiSzM0WlVPRlFCWDdOMiIsImxvZ2luX2NvdW50IjoyfQ.x6QRERZ9S0KITzHI8wXFhITlXb4cWs_MXttRWX2ZO4o' \
  --cookie '_limebike-web_session=Z2RnYWZlUi9Ybzd1cUpBRC9UcnBaelFsVjV5aE9MYnV4QldLL1p0ZzNKNmxQL3A1dTRLb3hXUXBmMzlzM2NQU3FmVXI2M1BWQmlEb1VWTm1yWmRaYkVsTVZ3Yjg2MnB1dXh3QWp5TDRYb1puL0ZrQmg2TDFzbThabUZoYUFQNlNHbHN6Y2l1bVR0YXZOSmFvalVDWHI4SFk1dVpUbVY5TDVmb3BvUGR3L3ZBbndNcXQzV2htQi9rUHBWODFDV2VTZnk5OG5peHFMclhkVVlUeTBXajRxT05aYnBWckFTcGxZZ1haeWtOcW9zNHhLY3FjYUhnTk1xL09CU0tBOGJmRkF3WWpHU1FmZTdlSCtEQlM4VlQ4T0l3RVZ5UWJma1lQY0V5cDRBN1YwMXkyZEhOSy9TU0RSdUZiYUlrYTdkdWh5aVNlL211V3hMbmszMk90bEQwZ3RnPT0tLUF4N3dzRG9xT0xXZnZreVlOR1NaL3c9PQ%3D%3D--21a30cf41170d4da4501b4cf0382ae53d8ee1ba7'
```

### The result of data

#### Seoul
```bash
{
  "data": {
    "id": "views::mapview",
    "type": "map_view",
    "attributes": {
      "user": {
        "id": "K34ZUOFQBX7N2",
        "type": "users",
        "attributes": {
          "token": "K34ZUOFQBX7N2",
          "phone_number": "821064816641",
          "email_address": null,
          "has_verified_email_address": false,
          "name": "Lime Rider",
          "given_name": "Lime",
          "surname": "Rider",
          "default_payment_method": null,
          "referral_code": "RTERXSC",
          "num_trips": 0,
          "edu": false,
          "subscription_item_states": [
            
          ],
          "promotion_notification": true,
          "donation_profile": {
            "id": "7AIBH7KWDJCLH",
            "type": "donation_profiles",
            "attributes": {
              "donation_type": "none",
              "donation_organizations": [
                
              ],
              "total_donation_amount": {
                "currency_code": "USD",
                "amount": 0,
                "amount_str": "0.0",
                "currency_symbol": "$",
                "display_string": "$0"
              },
              "total_donation_amount_cents": null,
              "currency": null
            }
          },
          "juicer_profile_status": null,
          "juicer_profile_initial_activated_at": null,
          "pod_vehicle_banner_status": "lime_pod_submit_docs",
          "juicer_referral_type": null,
          "accepted_user_agreement_version": 2,
          "accepted_compliance_version": 1,
          "new_juicer_earnings_amount": {
            "currency_code": "USD",
            "amount": 150,
            "amount_str": "150.0",
            "currency_symbol": "$",
            "display_string": "$150"
          },
          "juicer_referral_amount": null,
          "balance": {
            "currency_code": "KRW",
            "amount": 0,
            "amount_str": "0.0",
            "currency_symbol": "\u20a9",
            "display_string": "\u20a90"
          },
          "pending_balance": {
            "currency_code": "USD",
            "amount": 0,
            "amount_str": "0.0",
            "currency_symbol": "$",
            "display_string": "$0"
          },
          "new_juicer_earnings_promo_amount": "150",
          "new_juicer_earnings_promo_amount_cents": 15000,
          "new_juicer_earnings_promo_amount_cent": 15000,
          "new_juicer_earnings_promo_currency": "KRW",
          "juicer_referral_amount_cents": null,
          "juicer_referral_currency": null,
          "balance_cents": 0,
          "pending_balance_cents": 0,
          "currency": "USD",
          "show_group_ride": false,
          "id_verification_pending": false
        }
      },
      "regions": null,
      "zones": null,
      "zone_stylings": null,
      "bike_clusters": null,
      "bikes": null,
      "selected_bike": null,
      "parking_spots": null,
      "icons": null,
      "current_level": "subregion",
      "levels": {
        "region": 7,
        "subregion": 11,
        "city": 14
      },
      "most_recent_trip": null,
      "banner": {
        "id": "TROIBPVKM5UFS",
        "type": "banners",
        "attributes": {
          "text": "Lime-S Tutorial",
          "button_action": "app_link",
          "button_text": "OK",
          "button_link": "how_to_ride_scooter",
          "icon_url": null,
          "text_color": null,
          "background_color": null,
          "button_text_color": null,
          "button_text_background_color": null
        }
      },
      "donation_organization": null,
      "parking_spots_radius_meters": 20
    }
  },
  "meta": {
    "latest_user_agreement_version": "2",
    "min_ios_version": "2.11.0",
    "min_android_code": 93,
    "flags": "IOS_VERSION_V1.0,ANDROID_VERSION_V1.0",
    "groups": {
      "area_rate_plan_on_scanner": true,
      "enable_promo_notification_optout": true,
      "show_auto_reload": true,
      "map_levels_v1": true,
      "apple_pay": true,
      "show_lock_indicator": false,
      "map_balance_icon": false,
      "force_location_permission_v1": false,
      "unlock_button_group": "white_bar",
      "braze_integration": true,
      "ring_button_group": "louder_with_tooltip",
      "default_to_unlock_group": "control",
      "take_photo": "find_my_ride",
      "show_battery_level_on_map": true,
      "unlock_confirmation": false,
      "short_stop": true,
      "bluetooth_unlock": true,
      "lime_t_bluetooth_short_stop": true,
      "parked_or_not": false,
      "branch_link_referral": true,
      "persist_rate_ride": true,
      "no_header_map": true,
      "donation_group": "control",
      "fetch_end_trip_experience": false,
      "long_pause_group": false,
      "group_ride": false,
      "group_ride_v2": false,
      "group_ride_max_rider_cap": "5",
      "group_ride_max_guest_cap": "10",
      "paypal_payment_method": false,
      "enable_stripe_sca_flow": true,
      "id_scanner": "google_vision",
      "id_scan_show_manual_delay_sec?": 15,
      "new_method_completing_trip": true,
      "cvv_optional": false,
      "payment_creation_ui": true,
      "payment_billing_address": false,
      "payment_cardholder_name": false,
      "payment_zip_code": false,
      "payments": {
        "cvv_optional": false,
        "payment_creation_ui": true,
        "payment_billing_address": false,
        "payment_cardholder_name": false,
        "payment_zip_code": false,
        "payment_card_io_scan": false
      },
      "lime_t_whitelisted": true,
      "map_design_v3": false,
      "scooter_reservation": true,
      "pod_reservation": true,
      "use_moshi": false,
      "android_trip_events_refactor": false,
      "android_how_to_ride_tutorial": true,
      "timeout_retry": false,
      "cancel_reserve_red_button": true,
      "show_loyalty": true,
      "show_loyalty_spend_points": false,
      "show_self_help": false,
      "zone_messaging_enabled": false,
      "ride_history_with_pagination": false,
      "map_style_with_poi": false,
      "comfort_ride_enabled": false,
      "customized_speed_cap_enabled": false,
      "new_relic_logging_enabled": false,
      "recommend_nearby_bike_v2": false,
      "juicer_satellite_mode": true,
      "juicer_level_2": true,
      "juicer_reservation_v1_ios": false,
      "juicer_reservation_v1_android": false,
      "juicer_reservation_collected_limes_ios": false,
      "juicer_reservation_collected_limes_android": false,
      "juicer_reserved_android_filter": false,
      "juicer_reserved_ios_filter": false,
      "ios_juicer_rebalance_v1": false,
      "android_juicer_rebalance_v1": false,
      "juicer_hide_scooter_details": false,
      "enable_juicer_mock_gps_blocker": true,
      "juicer_earnings_notification": true,
      "enable_juicer_settings": true,
      "enable_juicer_in_app_message": true,
      "ios_juicer_multi_task_v1": true,
      "android_juicer_multi_task_v1": true,
      "complete_trip_before_take_photo": true,
      "android_upload_juicer_attributes": true,
      "enable_juicer_endpoint_v2": true,
      "juicer_bluetooth_unlock": false,
      "android_enable_backend_driven_cancel_task": true,
      "android_tooltip_v2": true,
      "android_enable_bulk_scan_of_deploy_tasks": null
    },
    "trip_id": null,
    "trip_status": null,
    "group_id": null,
    "group_ride_status": null,
    "notifications": [
      
    ],
    "messages": [
      {
        "message_token": "WWSXDGHWFABTM",
        "title": "Ride More, Pay Less",
        "image_title": "image_title",
        "lifecycle": "asap",
        "body": "Receive unlimited free unlocks for only \u20ac4.99 with the Lime Week Pass.",
        "user_input": false,
        "image_url": "https:\/\/limebike-web-public-assets.s3-us-west-1.amazonaws.com\/messages\/g2cmdunhe0n%403x.png",
        "image_medium_url": "https:\/\/limebike-web-public-assets.s3-us-west-1.amazonaws.com\/messages\/w4ujyd41e4%402x.png",
        "image_small_url": "https:\/\/limebike-web-public-assets.s3-us-west-1.amazonaws.com\/messages\/dfchuo6v49o%401x.png",
        "layout_type": "basic",
        "button_action": "app_link",
        "button_text": "Learn More",
        "text_input_hint": "",
        "option_text": "",
        "button_action_link": {
          "link": "limebike:\/\/limelab?url_to_open=https:\/\/webviews.lime.bike\/module\/limepass"
        },
        "button_action_email": null
      }
    ],
    "country_code": "",
    "user_agreement_version": 2,
    "user_agreement_country_code": "",
    "need_to_show_agreement": false,
    "user_agreement_url": "https:\/\/li.me\/user-agreement\/",
    "user_agreement_title": "We've Updated Our User Agreement",
    "user_agreement_message": "By tapping \"I Agree\" You confirm that You have read, understood, and agreed to Lime\u2019s updated User Agreement.",
    "user_agreement_primary_button": "I Agree",
    "user_agreement_view_terms_button": "View Agreement",
    "need_to_show_group_ride_agreement": true
  }
}
```




#### sample
{
  "data": {
    "id": "views::mapview",
    "type": "map_view",
    "attributes": {
      "user": {
        "id": "K34ZUOFQBX7N2",
        "type": "users",
        "attributes": {
          "token": "K34ZUOFQBX7N2",
          "phone_number": "821064816641",
          "email_address": null,
          "has_verified_email_address": false,
          "name": "Lime Rider",
          "given_name": "Lime",
          "surname": "Rider",
          "default_payment_method": null,
          "referral_code": "RTERXSC",
          "num_trips": 0,
          "edu": false,
          "subscription_item_states": [
            
          ],
          "promotion_notification": true,
          "donation_profile": {
            "id": "7AIBH7KWDJCLH",
            "type": "donation_profiles",
            "attributes": {
              "donation_type": "none",
              "donation_organizations": [
                
              ],
              "total_donation_amount": {
                "currency_code": "USD",
                "amount": 0,
                "amount_str": "0.0",
                "currency_symbol": "$",
                "display_string": "$0"
              },
              "total_donation_amount_cents": null,
              "currency": null
            }
          },
          "juicer_profile_status": null,
          "juicer_profile_initial_activated_at": null,
          "pod_vehicle_banner_status": "lime_pod_submit_docs",
          "juicer_referral_type": null,
          "accepted_user_agreement_version": 2,
          "accepted_compliance_version": 1,
          "new_juicer_earnings_amount": {
            "currency_code": "EUR",
            "amount": 100,
            "amount_str": "100.0",
            "currency_symbol": "\u20ac",
            "display_string": "\u20ac100"
          },
          "juicer_referral_amount": null,
          "balance": {
            "currency_code": "KRW",
            "amount": 0,
            "amount_str": "0.0",
            "currency_symbol": "\u20a9",
            "display_string": "\u20a90"
          },
          "pending_balance": {
            "currency_code": "USD",
            "amount": 0,
            "amount_str": "0.0",
            "currency_symbol": "$",
            "display_string": "$0"
          },
          "new_juicer_earnings_promo_amount": "100",
          "new_juicer_earnings_promo_amount_cents": 10000,
          "new_juicer_earnings_promo_amount_cent": 10000,
          "new_juicer_earnings_promo_currency": "EUR",
          "juicer_referral_amount_cents": null,
          "juicer_referral_currency": null,
          "balance_cents": 0,
          "pending_balance_cents": 0,
          "currency": "USD",
          "show_group_ride": true,
          "id_verification_pending": false
        }
      },
      "regions": null,
      "zones": [
        {
          "id": "2KA6UWD75E46I",
          "type": "zones",
          "attributes": {
            "name": "Flughafen Tempelhof",
            "polyline": "cjg_IqtupA__@Yk\\qRyGas@DkZlRuvAls@cLdGnQdPra@~Eha@mBnc@u]tkA",
            "category": "no_parking_zone",
            "icon_latitude": "52.474415",
            "icon_longitude": "13.40318",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "PKRTNCOTX6S6W",
          "type": "zones",
          "attributes": {
            "name": "Tempelhofer Feld",
            "polyline": "s`g_I}mupARkShQ{p@`Kuf@cJylAaKbAsIkHaBgS{FjBmb@pMXpFqCf@oA~NbBtLiP`]_FeCmCdRiArOoAx[_Aj`@[bOQ~Cx@@p@\\f@d@Vf@\\`APfBDnCdqAP",
            "category": "no_parking_zone",
            "icon_latitude": "52.474685",
            "icon_longitude": "13.40329",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "HSSWN5HQXWHMQ",
          "type": "zones",
          "attributes": {
            "name": "Volkspark Hasenheide",
            "polyline": "ggj_Igt|pAvX?b@tLvH?f@rIuNblAeNgAcIoHuHz@nHimAlBcL",
            "category": "no_parking_zone",
            "icon_latitude": "52.484435",
            "icon_longitude": "13.414805",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "CQWL3BOSE6MRS",
          "type": "zones",
          "attributes": {
            "name": "BR: Volkspark Hasenheide",
            "polyline": "mvj_IgwwpA|MtA^}WhGCpFpEnAaPzAaM~MqdAlAeL?cCo@{HCu@eIPc_@KqE`m@oBdm@W~s@",
            "category": "no_parking_zone",
            "icon_latitude": "52.48451",
            "icon_longitude": "13.409215",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "LMC54PZDDDBZI",
          "type": "zones",
          "attributes": {
            "name": "BR: Tivoliplatz",
            "polyline": "myj_I_tspA|WYn@kJKwBsHCOyGyBGVeI_@kHL{AoDiA]|EgA`DmE}@zAxf@",
            "category": "no_parking_zone",
            "icon_latitude": "52.48746",
            "icon_longitude": "13.38079",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "SG6K5BJ7VXCUE",
          "type": "zones",
          "attributes": {
            "name": "BR: Treptower",
            "polyline": "wyk_IomdqA~LlJdKxDru@{oAeYux@uArLgF|IuFrAeFnHeGxOeGfb@mLl_@",
            "category": "no_parking_zone",
            "icon_latitude": "52.488055",
            "icon_longitude": "13.471125",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "C75K6JWYFHD6X",
          "type": "zones",
          "attributes": {
            "name": "BR: Freidhofsverwaltung",
            "polyline": "qcl_IgewpA@lGz@|R~BxCnBbBnAbA]oLq@sYoHt@",
            "category": "no_parking_zone",
            "icon_latitude": "52.49514",
            "icon_longitude": "13.39198",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "XORFA6OCBAIPS",
          "type": "zones",
          "attributes": {
            "name": "BR: Bocklerpark",
            "polyline": "unl_IslypAtFlE^eBAgDRaEf@eE|@{I@gAVmCb@aBj@iIA{GW?DdIg@vFeAlAkAG[jBjAr@_BbH{C\\uAbHExH",
            "category": "no_parking_zone",
            "icon_latitude": "52.495349999999995",
            "icon_longitude": "13.41357",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "J2QSH56BZ3VHN",
          "type": "zones",
          "attributes": {
            "name": "BR: Sommerbad Kreuzberg",
            "polyline": "iol_IcmwpApDyZ|AaZ_@_Ao@a@mFwDAxv@n@|F",
            "category": "no_parking_zone",
            "icon_latitude": "52.49741",
            "icon_longitude": "13.40127",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "NEA24D35C75J2",
          "type": "zones",
          "attributes": {
            "name": "BR: Mondh\u00fcgel",
            "polyline": "otk_Iiq`qAsGaKcYnnAR~CfBS\\{DxAiA~BtBdVibA",
            "category": "no_parking_zone",
            "icon_latitude": "52.496455",
            "icon_longitude": "13.4381",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "YNT5HNPV2BXLB",
          "type": "zones",
          "attributes": {
            "name": "Rocket Tower",
            "polyline": "ifn_IwvvpAnBSQaIoBRP`I",
            "category": "no_parking_zone",
            "icon_latitude": "52.506535",
            "icon_longitude": "13.393455",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "BZRCIWWS5FHUL",
          "type": "zones",
          "attributes": {
            "name": "Ernst-Reuter-Platz",
            "polyline": "cmo_I}whpAJVVJn@Jr@QVo@L_@Fg@@w@C{@Gg@Ki@Ya@UU[G]BYLOPUb@On@Gl@?j@Dt@Hr@Tb@",
            "category": "no_parking_zone",
            "icon_latitude": "52.512605",
            "icon_longitude": "13.32187",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "4RVJ6VVQDGCTF",
          "type": "zones",
          "attributes": {
            "name": "Tiergarten sudwest",
            "polyline": "uyn_IiqnpA}TnDqBhGxBj_AzH~@vI}Q}Hi]~I_^",
            "category": "no_parking_zone",
            "icon_latitude": "52.51191",
            "icon_longitude": "13.34436",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "SZFXBQWQBKI7J",
          "type": "zones",
          "attributes": {
            "name": "Berlin - Denkmal der Juden",
            "polyline": "kvo_I{yspA|Fn@}AqNcEhBb@xI",
            "category": "no_parking_zone",
            "icon_latitude": "52.513915",
            "icon_longitude": "13.378745",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "MPPJE6CSCCMQA",
          "type": "zones",
          "attributes": {
            "name": "Denkmal f\u00fcr die ermordeten Juden",
            "polyline": "ymo_ImwspAkBcPKBoEhBNx@RdIbHt@",
            "category": "no_parking_zone",
            "icon_latitude": "52.51391",
            "icon_longitude": "13.37872",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "BA6SVCT5LRQSX",
          "type": "zones",
          "attributes": {
            "name": "BR: Ermordeten Juden",
            "polyline": "cxo_IeetpAL`BTjH~Df@fBPmB_Q_FxB",
            "category": "no_parking_zone",
            "icon_latitude": "52.513915",
            "icon_longitude": "13.37871",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "6GDFDNVXSKTSU",
          "type": "zones",
          "attributes": {
            "name": "Tiergarten sudost",
            "polyline": "apo_IgqnpApS_FEwTIo\\i@_YoEoc@oFse@iPqCi@jDbHfrCvCfJ",
            "category": "no_parking_zone",
            "icon_latitude": "52.512915",
            "icon_longitude": "13.363875",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "NBAEL2IZX3AFU",
          "type": "zones",
          "attributes": {
            "name": "TIERGARTEN 2",
            "polyline": "cxo_IcfnpAkCpGsC`JnA|BlAnb@i@hCzAxBp@f@r@Tn@?`@Gl@E^?qCi`Ac@kB",
            "category": "no_parking_zone",
            "icon_latitude": "52.515005",
            "icon_longitude": "13.34345",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "RDZ3H2SZY6IBA",
          "type": "zones",
          "attributes": {
            "name": "Berlin - Brandenburger Tor",
            "polyline": "ehp_IsjtpAdG{AlA~Ry@Vk@dBg@TW[y@}@g@CkAwQ",
            "category": "no_parking_zone",
            "icon_latitude": "52.51646",
            "icon_longitude": "13.37891",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "UZRERXUA2CDW4",
          "type": "zones",
          "attributes": {
            "name": "BABEL PLTZ",
            "polyline": "wep_I{kvpAbEa@M{MDmDE]`Dg@MuKiLpA~Av`@",
            "category": "no_parking_zone",
            "icon_latitude": "52.5163",
            "icon_longitude": "13.393755",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "BG5O6YE3CZ3NS",
          "type": "zones",
          "attributes": {
            "name": "Tiergarten nordost",
            "polyline": "g`p_IcgrpAmH}CExAlAnB_@pd@LpNdCzRi@jOnI|SsDqnB",
            "category": "no_parking_zone",
            "icon_latitude": "52.51636",
            "icon_longitude": "13.36108",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "DE7SYP3UXCBOA",
          "type": "zones",
          "attributes": {
            "name": "ENGLISCHER GARTEN",
            "polyline": "qzo_IofnpAcJ~XsCyAHgA_@qGDcAb@yCXkBbAsHlDv@F{@^}AVuAj@_ArAlCPnD?fDFBAB",
            "category": "no_parking_zone",
            "icon_latitude": "52.51644",
            "icon_longitude": "13.348185",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "TCJIBRG6Y2PHA",
          "type": "zones",
          "attributes": {
            "name": "BR: Lustgarten",
            "polyline": "_up_I_vwpA|HcGAwAmBwHsDpD{CbD`BtF`@fA",
            "category": "no_parking_zone",
            "icon_latitude": "52.51889",
            "icon_longitude": "13.39925",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "4AIMHBLCKGORB",
          "type": "zones",
          "attributes": {
            "name": "BR: Berline Dom",
            "polyline": "myp_Ii`xpA`BaBx@{@vD_EkAoEsAbAaA|@wAtBuAbDz@pC",
            "category": "no_parking_zone",
            "icon_latitude": "52.51937",
            "icon_longitude": "13.400645",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "5XB4Z5VDDXTJF",
          "type": "zones",
          "attributes": {
            "name": "BR: Bundestag",
            "polyline": "_}p_Ia|qpAxE`MK}WDoWaFFAvOLhQ",
            "category": "no_parking_zone",
            "icon_latitude": "52.520135",
            "icon_longitude": "13.369555",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "JADGX4N37FXEU",
          "type": "zones",
          "attributes": {
            "name": "Berlin - Kongress Area",
            "polyline": "_~p_Iqe{pAv@aAzAiB_@k@KMg@s@y@cAUWu@tDe@o@kAu@YhAbEnEJJ@?",
            "category": "no_parking_zone",
            "icon_latitude": "52.520955",
            "icon_longitude": "13.416385",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "ZHKEAFCVUVL6W",
          "type": "zones",
          "attributes": {
            "name": "BR: Kleiner Tiergarten",
            "polyline": "w_r_IwbmpArAXhA\\hCe`@oDmAM`BaB@?hPAvEEvE",
            "category": "no_parking_zone",
            "icon_latitude": "52.52546",
            "icon_longitude": "13.34589",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "V5USPAI7UL7JI",
          "type": "zones",
          "attributes": {
            "name": "BR: Keliner Tiergarten 2",
            "polyline": "{_r_Is`mpAKxNnBTv@yM{Cs@",
            "category": "no_parking_zone",
            "icon_latitude": "52.52586",
            "icon_longitude": "13.34166",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "2NE4B7POA3KKW",
          "type": "zones",
          "attributes": {
            "name": "Hackische H\u00f6fe",
            "polyline": "_xq_I}wxpAlEdDRtDAjHiNjEpEgRt@kF",
            "category": "no_parking_zone",
            "icon_latitude": "52.52506",
            "icon_longitude": "13.4009",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "SKU7FER257BSM",
          "type": "zones",
          "attributes": {
            "name": "BR: Ottopark",
            "polyline": "ywq_ImqkpAwDaV?Sq@Tk@HIxBZPZvLp@@DXEjC~Cp@Bk@RY",
            "category": "no_parking_zone",
            "icon_latitude": "52.525645",
            "icon_longitude": "13.337145",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "HATCM55YN6KPP",
          "type": "zones",
          "attributes": {
            "name": "Volkspark Friedrichshain",
            "polyline": "ikr_Iyc}pAvC}JzDgHhCuE|BwDdCuEtByEn@kDGqNoAaMuB]D_CZeCoBsKkD|CaCmNRuA|AwBeFqGcBpAoSbUrLbUcDtEzG|jA",
            "category": "no_parking_zone",
            "icon_latitude": "52.527175",
            "icon_longitude": "13.435755",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "BRYRVFFCMPWSR",
          "type": "zones",
          "attributes": {
            "name": "BR: Freidensglocke",
            "polyline": "{kr_Iqb}pAj@QdBiGvAiEpGgL`CkDjEuJdBkFGaG{AeCjAwDg@?_CpAmABcAcAi@aB{@`@g@nBa@xAaAz@gCoH[?{@kDRcJt@CDaB|BuC~BuCaCaMcDzDs@]oCeMcQzRdMfUIfAaCdCvGnlA",
            "category": "no_parking_zone",
            "icon_latitude": "52.52727",
            "icon_longitude": "13.435285",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "LPLMAGPD3RDQW",
          "type": "zones",
          "attributes": {
            "name": "BR: Freidensglocke",
            "polyline": "{kr_Iqb}pAj@QdBiGvAiEpGgL`CkDjEuJdBkFGaG{AeCjAwDg@?_CpAmABcAcAi@aB{@`@g@nBa@xAaAz@gCoH[?{@kDRcJt@CDaB|BuC~BuCaCaMcDzDs@]oCeMcQzRdMfUIfAaCdCvGnlA",
            "category": "no_parking_zone",
            "icon_latitude": "52.52727",
            "icon_longitude": "13.435285",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "FTRL76MSNINWZ",
          "type": "zones",
          "attributes": {
            "name": "BR: Fritzschloss-park",
            "polyline": "e~r_IcaopAbDiEt@Sf@bAjGwE`AhCzBgBMqAlBkAV`AbGyEgIs^_Bv@kBcIoYxRp@nNfFzW",
            "category": "no_parking_zone",
            "icon_latitude": "52.52904",
            "icon_longitude": "13.358115",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "SE3CJZ7MUOSTW",
          "type": "zones",
          "attributes": {
            "name": "State Park Volkspark",
            "polyline": "gjs_IcbdqAl@mDl@iBLaAOkAwAuFKUc@S}AiHu@qCUmAD_@aAkCy@iCGAGBMHgGfDMRKb@U`BYjA]z@IBGDCV}@xEaA~DaCdJy@|CgC~I|@|@BRAVIT?N@HBHLNpD`Ef@aBvAbBz@lAt@CfACCYOIMS?e@xBQ?m@Fm@\\qFr@kJHm@HQHD`L|DJFDK",
            "category": "no_parking_zone",
            "icon_latitude": "52.53575",
            "icon_longitude": "13.463105",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "C6E35EUGR22HY",
          "type": "zones",
          "attributes": {
            "name": "Kulturbrauerrei",
            "polyline": "c{t_Ic_{pAg@WQSbAk@IvA",
            "category": "parking_zone",
            "icon_latitude": "52.54094",
            "icon_longitude": "13.41464",
            "show_icon": false,
            "zone_styling_id": "174"
          }
        },
        {
          "id": "ZCTG7IETBM2QF",
          "type": "zones",
          "attributes": {
            "name": "BR: Volkspark Prenzlauer",
            "polyline": "igt_IudfqAkLzGxG`KEnB_Mha@nGvF}Jd_@pDbHrAcD^sHpDoMtElEh@gBvA~BRuAtF`@bBaV`MrDvBiKeLec@iGhCsA}LmBhC{C{K",
            "category": "no_parking_zone",
            "icon_latitude": "52.53682",
            "icon_longitude": "13.463005",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "HJ3LPW3ONV6WY",
          "type": "zones",
          "attributes": {
            "name": "BR: Sportforum Berlin",
            "polyline": "e_t_I_qfqAeFoXaCfBuF{R`CqCqDiNgRyd@iNhw@gDa@}ApNdMfQbGbH|BYjLdTjMcHbHsH",
            "category": "no_parking_zone",
            "icon_latitude": "52.541405",
            "icon_longitude": "13.480085",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "UFOEV3AQB4QWA",
          "type": "zones",
          "attributes": {
            "name": "Mauerpark",
            "polyline": "}xt_I{zxpAs@wEq@{FuAeMiB|@EQYaCo@aGeAsJCMGGO?i@VmA^iBv@}DzAmGjCLlBVnCj@lHj@hGoCx@wBp@`@vHV~Gl@lNFbBJRFpBdCu@PEBk@l@]dA}ApAS@LTlAvCU|ACfAy@rAaAhAm@LXdGcFTr@HZlBuAu@{Dw@aE",
            "category": "no_parking_zone",
            "icon_latitude": "52.54344",
            "icon_longitude": "13.405295",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "RRTRZMW57S224",
          "type": "zones",
          "attributes": {
            "name": "BR: Mauerpark",
            "polyline": "}fu_IgnzpAoUdIjC~XoG~BvBvc@tNcDRqGtSqJeEm[cBP{C{V",
            "category": "no_parking_zone",
            "icon_latitude": "52.54371",
            "icon_longitude": "13.40557",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "3SBMWED2IW5MY",
          "type": "zones",
          "attributes": {
            "name": "BR: Humboldthai",
            "polyline": "yzu_I{ttpAxAgGjBbDj@bCxAt@~B|D~FgLkByIeJkf@qUdP@fV`BvFdGrJjB_D",
            "category": "no_parking_zone",
            "icon_latitude": "52.54528",
            "icon_longitude": "13.385755",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "VOFIRCNCK45PF",
          "type": "zones",
          "attributes": {
            "name": "Park Humboldthain",
            "polyline": "ilu_IeltpAbGqLi@oAaBqIcEmTmCyNuBzA}CxBqEjDeCxA}AfAErW`@|@|AfEfBjD~BfDhB_D~AaG`DfHr@FdDzE",
            "category": "no_parking_zone",
            "icon_latitude": "52.545265",
            "icon_longitude": "13.38578",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "3M45GSWPR63XD",
          "type": "zones",
          "attributes": {
            "name": "BR: St. Johanis Kirschof",
            "polyline": "u}u_IqdmpAcDlE~CvIYrCRl@yFdJeDzHlGrL`JwSDo@n@?`CxH_DfFwC|GCbBe@UY^fBjCt@u@nAsAbBy@dDwAnCaAt@m@nCyEmYgq@",
            "category": "no_parking_zone",
            "icon_latitude": "52.545295",
            "icon_longitude": "13.33805",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "PWHPC7ELYLMU6",
          "type": "zones",
          "attributes": {
            "name": "Humboltdhain",
            "polyline": "usu_I}hvpA{R|N}EvF`CfOzTb\\|LyUaLgm@",
            "category": "no_parking_zone",
            "icon_latitude": "52.54585",
            "icon_longitude": "13.384865",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "5VHIPEIJC2WQT",
          "type": "zones",
          "attributes": {
            "name": "BR: Urnenfreidhof seestrasse",
            "polyline": "oxv_IixnpAcUkh@uFdMfVva@jAuCl@v@vAuC",
            "category": "no_parking_zone",
            "icon_latitude": "52.553025",
            "icon_longitude": "13.354595",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "VU76ZRZOGDFX6",
          "type": "zones",
          "attributes": {
            "name": "Weissensee",
            "polyline": "sxw_IaucqA|AlAh@cCvA|AtB_HHOHKh@@rBf@vEbAXgDe@Y^_D\\H`@sDlDbAkAcGk@_CqBsFgAaDoA}BqAcAKbASCEVMG@QqBu@Gl@e@GSGIzASBEb@kAAuAn@c@j@[|@}@_AQIo@lCAvAPDA`D|AC@|BUd@mBFYFBzDpCAA^QBFXOL@bBGd@LTAP@Z~@n@u@xDNVM|@",
            "category": "no_parking_zone",
            "icon_latitude": "52.55365",
            "icon_longitude": "13.46272",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "NTVDZNTYRUFOR",
          "type": "zones",
          "attributes": {
            "name": "BR: Schillerpark",
            "polyline": "azw_I}wopA{DhIsAqC}@oDbBsBSe@eBXEwBVi@u@oD[_Cq@aEm@JZrBcDfADxEtB~K{CdCXtAlDkDlA|ArClLLzG[??lCmAvBa@i@g@v@|B`EnBfBrA`BbAzDnP{]iOmW",
            "category": "no_parking_zone",
            "icon_latitude": "52.556405",
            "icon_longitude": "13.354475",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "ECWDMEZQC6HPI",
          "type": "zones",
          "attributes": {
            "name": "BR: Schillerpark 2",
            "polyline": "ohx_IgsnpAuMdYzKjRxMcYs@qCe@cAu@u@qBiB_DwF",
            "category": "no_parking_zone",
            "icon_latitude": "52.558455",
            "icon_longitude": "13.347435",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "BRUJQHTFLD6WC",
          "type": "zones",
          "attributes": {
            "name": "BR: Sch\u00e4fersee",
            "polyline": "eqy_IegopAj@Km@gJ|FoB^kM^wBFeEIgFoAaEoAe@FiCs@\\c@tAeChCk@uAiAjMtDre@",
            "category": "no_parking_zone",
            "icon_latitude": "52.564465",
            "icon_longitude": "13.35893",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        },
        {
          "id": "2HNJSZOX5NE5O",
          "type": "zones",
          "attributes": {
            "name": "Berlin service zone",
            "polyline": "}qu_IarlpAaJoMmYkp@epA|xCuMkx@jM{w@nFs^H_UHyh@gCuWiAyJsA}_ARmTHyeA}Oo\\hAoaAmHe_@qDuaBIsHdSxCvv@}L`YqGf`Ac{CpDs@nVha@hm@en@ra@s^bHoc@dGwBr@oy@fJuCrA{e@x@eI~Nz@r@iGjMmbCtm@pJz]tEteAhoCcZjaCzUfQ|s@olAlY`cBhY?lSbjA|d@cAdElgAssAng@vA|i@kV_J_OtEsHzgBc@~u@zErw@bjAzBwDpf@Ydu@uEdPsXtP_FzGeO|b@`CdIbIdThIxUyGbgAaChoCqw@ztAck@|t@E|i@_w@hYoMfSu@eGVyE{T_Fss@`Iqo@w\\_Yo{@iZykC_LqjB{m@{g@AO",
            "category": "service_zone",
            "icon_latitude": "52.51567",
            "icon_longitude": "13.394105",
            "show_icon": false,
            "zone_styling_id": "116"
          }
        },
        {
          "id": "DKNIBFBGB6453",
          "type": "zones",
          "attributes": {
            "name": "(BELIN) NO PARKING ZONE 2",
            "polyline": "_```IkqupA|rHkfDvJqnBds@_fB`y@{t@xf@cp@lZ}gA|q@lEfb@ha@pc@uaBnx@lEmZ`dCdUha@fs@glAlZppAlZ?rRbjA|d@cApExeA}sAvg@rA|i@oVwIuNlEoGnaB}@l}@pExv@xjAhCvpB_K|rGou@ogAk{c@mx`@b`Eo\\hv_@",
            "category": "no_parking_zone",
            "icon_latitude": "52.503235",
            "icon_longitude": "13.48532",
            "show_icon": false,
            "zone_styling_id": "1"
          }
        }
      ],
      "zone_stylings": null,
      "bike_clusters": null,
      "bikes": [
        {
          "id": "ET-E4N6UDNH6253AY6QJRLUDFMBM36CLU3IN6DKTPI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-GSH",
            "latitude": 52.500401,
            "longitude": 13.399789,
            "last_activity_at": "2019-10-14T10:41:28.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 17300,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "GSH",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-F7667HC54FQQSCT6PXFA2EIUNPE57LLARQUAELQ",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-GZB",
            "latitude": 52.500829,
            "longitude": 13.401576,
            "last_activity_at": "2019-10-14T10:36:22.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 38623,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "GZB",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-V75O6VA2E5ML4TAIVMXC635EEV42I7UTZXNS2XY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-SAH",
            "latitude": 52.501397,
            "longitude": 13.399623,
            "last_activity_at": "2019-10-14T10:41:39.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 17702,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "SAH",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-UIPADL62UVPMJZE6V3ESQRDDTTAFHVJFZF3KJLY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-ARV",
            "latitude": 52.498426,
            "longitude": 13.400117,
            "last_activity_at": "2019-10-14T10:39:30.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "ARV",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-TBSJB4ZX4XLZXF7HZ3LODALSUB67V7NRQE53SWA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-JGL",
            "latitude": 52.500804,
            "longitude": 13.396505,
            "last_activity_at": "2019-10-14T10:41:04.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 39830,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "JGL",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-Y5EXNFDPOMHDLLIJFHCET3MDUQARGOFTQW4XYHY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-LUD",
            "latitude": 52.499317,
            "longitude": 13.403692,
            "last_activity_at": "2019-10-14T10:42:00.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "low",
            "meter_range": 11265,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "LUD",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-XEL3I5T4WC45HP4VYK2Y7NDBH7WZAJJFJFEHOLY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-RBR",
            "latitude": 52.499764,
            "longitude": 13.395554,
            "last_activity_at": "2019-10-14T10:39:51.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "RBR",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-TPWWMSFASLGKJDMZM5JMFDEMQYJGEGT66XA2QFA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-SDK",
            "latitude": 52.499654,
            "longitude": 13.395522,
            "last_activity_at": "2019-10-14T10:37:57.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "SDK",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-UGZUVCV7MDAMV7YX65YBEAU2RPQDCDC3UXETRCA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-FVY",
            "latitude": 52.499814,
            "longitude": 13.39545,
            "last_activity_at": "2019-10-14T10:41:06.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "FVY",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-W7MP6FOBF3ZJ2FHYGKPYXF6V73PMP4VG45UFGKY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-GCH",
            "latitude": 52.499633,
            "longitude": 13.395461,
            "last_activity_at": "2019-10-14T10:36:19.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "GCH",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-4UK3DCLRUY2QE6J7DYURQEGZUJRODLJ2B7DYARI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-ZXG",
            "latitude": 52.500512,
            "longitude": 13.395109,
            "last_activity_at": "2019-10-14T10:39:44.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 32588,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "ZXG",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-I5G3HVX63AXLF7ILB54DXMJ36RUJA5ERN4DUGIA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-MRA",
            "latitude": 52.500314,
            "longitude": 13.394668,
            "last_activity_at": "2019-10-14T10:37:49.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 19311,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "MRA",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-EYRSIA3Q3EAWLXQ52W44WDCTB2XD4SNMTNQ43HQ",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-NVR",
            "latitude": 52.500945,
            "longitude": 13.394833,
            "last_activity_at": "2019-10-14T10:34:17.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 20518,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "NVR",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-77INDIRKKFE2DI3S22JC4TIXY6KWPUHFEOTVHBY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-ZKK",
            "latitude": 52.497448,
            "longitude": 13.396584,
            "last_activity_at": "2019-10-14T10:38:00.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 18909,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "ZKK",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-VPWPNXNRMOQ2MVDXJ4OBQ3YFCYRFKZ22QDDCUMI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-GHW",
            "latitude": 52.500256,
            "longitude": 13.394348,
            "last_activity_at": "2019-10-13T12:42:18.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 29370,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "GHW",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-CGUQLD5ZQRBORXMPWQVDXHTI3RKFTIBF2NGZMWA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-RFB",
            "latitude": 52.500333,
            "longitude": 13.39435,
            "last_activity_at": "2019-10-13T11:40:25.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 25749,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "RFB",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-3FUDFRXX2S56RLTPZ7JBH25GDW47CL6WHRSLYBI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-YHS",
            "latitude": 52.503296,
            "longitude": 13.398572,
            "last_activity_at": "2019-10-14T10:41:22.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 24944,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "YHS",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-Z2YF23Q3H4R4STGMECKPRKTVIDVZAP6TCNV6RRA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-WLU",
            "latitude": 52.503283,
            "longitude": 13.398474,
            "last_activity_at": "2019-10-14T10:37:33.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 20518,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "WLU",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-54M73HIGQIDUR4ICQFMALCHJM3QXOIX7CHHB7NA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-PLL",
            "latitude": 52.503333,
            "longitude": 13.398485,
            "last_activity_at": "2019-10-14T10:40:44.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 16495,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "PLL",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-HFWCDELUIGVBSQ2PRLCR7GR7IHRI5CVTWZ2EJ7I",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-MSY",
            "latitude": 52.503377,
            "longitude": 13.39845,
            "last_activity_at": "2019-10-14T10:40:01.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "MSY",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-KNJGDPRFXXXZUGMNR7WDL3WO5TXR2BS3BISTZTY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-LSB",
            "latitude": 52.503392,
            "longitude": 13.398383,
            "last_activity_at": "2019-10-14T10:39:55.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "LSB",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-PHPC6DEQZKUHJURX4FEJZTXI6NQFQIMVEF6DYHY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-DLG",
            "latitude": 52.503413,
            "longitude": 13.398455,
            "last_activity_at": "2019-10-14T10:41:14.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 22128,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "DLG",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-YK3US6F42WLKAO4O3ZPHYX2BQKF5IQIRP7T6KOA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-THT",
            "latitude": 52.496613,
            "longitude": 13.401218,
            "last_activity_at": "2019-10-14T10:41:25.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 17702,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "THT",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-ZDJ326ZETC5H3B3HGCSDZNA42FXHJPGQN6K5XBY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-EFY",
            "latitude": 52.499717,
            "longitude": 13.40565,
            "last_activity_at": "2019-10-14T10:34:37.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 22128,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "EFY",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-2CMAT3X7DKVVOB3ENJG4RJZGYBEXVEQUNAC43OI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-PYH",
            "latitude": 52.496529,
            "longitude": 13.401382,
            "last_activity_at": "2019-10-14T10:41:03.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 22530,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "PYH",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-M4LLTQIOOVK6YJUSCUEVGVYSXOVKGKKM7MG4UJI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-LGW",
            "latitude": 52.500709,
            "longitude": 13.393855,
            "last_activity_at": "2019-10-14T10:37:06.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 31784,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "LGW",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-VJELBEUDJICY35HODYF5YD3YFHXGZ2XRE5MJM7I",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-JQF",
            "latitude": 52.496405,
            "longitude": 13.401224,
            "last_activity_at": "2019-10-14T10:37:13.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 26956,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "JQF",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-XSIXRRVUCLTIOEDZH3LC555O6EQ5XS57QAZJYSI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-DVR",
            "latitude": 52.499979,
            "longitude": 13.393529,
            "last_activity_at": "2019-10-14T10:39:32.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 17300,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "DVR",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-WZDLN6ZYE3USWCGUDN5Q5JPBQ52ADTCNKSNVNTA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-XDA",
            "latitude": 52.502304,
            "longitude": 13.394568,
            "last_activity_at": "2019-10-14T10:40:58.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "XDA",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-QRVWRRUDCGOUWMNS24E5LQWCAOHFZN2VNG5MZKQ",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-XGM",
            "latitude": 52.502301,
            "longitude": 13.394543,
            "last_activity_at": "2019-10-14T10:39:41.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "XGM",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-DAMRT5KJPL6IGHV7FXYLTAIIJUJ7WDB2WMUM3TQ",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-XFR",
            "latitude": 52.500604,
            "longitude": 13.39315,
            "last_activity_at": "2019-10-14T10:41:05.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 16495,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "XFR",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-IRDW7PVA5AI37QOYS2YMXCRVA4ETEIKQXTJLDTA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-MHC",
            "latitude": 52.49593,
            "longitude": 13.40011,
            "last_activity_at": "2019-10-14T10:39:30.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 29370,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "MHC",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-FPZLA7AL7UEKTHTN7RA2A4AZHT23GK22TLTJATI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-JRP",
            "latitude": 52.503586,
            "longitude": 13.403494,
            "last_activity_at": "2019-10-14T10:40:47.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 36209,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "JRP",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-CE27UUCK4553LNVOQT6BQCW6CDEP7O6DBTQPDAA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-CZR",
            "latitude": 52.503046,
            "longitude": 13.405492,
            "last_activity_at": "2019-10-14T10:37:22.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 30577,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "CZR",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-IERRIC57S3VUHK5CRZXJQDSUHEMILBS4DJ5BUIQ",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-XZY",
            "latitude": 52.495777,
            "longitude": 13.396896,
            "last_activity_at": "2019-10-14T10:40:05.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 28163,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "XZY",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-BJC4JJTK4US6OLSVHND7FG4SIA6RJZCHE4KVC3Y",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-CMG",
            "latitude": 52.504118,
            "longitude": 13.395858,
            "last_activity_at": "2019-10-14T10:37:59.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 34198,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "CMG",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-5GE7GLWHZCLBZX6YQX373SF7UOIZNMVWC5NG6OA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-SAK",
            "latitude": 52.499653,
            "longitude": 13.39182,
            "last_activity_at": "2019-10-14T10:34:47.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 34600,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "SAK",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-GRQ4JGY7ZJRQK2ALE6Z6EWA5JWJ7H7OTNKRS3GA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-PBR",
            "latitude": 52.504457,
            "longitude": 13.403406,
            "last_activity_at": "2019-10-14T10:39:05.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 18909,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "PBR",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-ZKADDEFSKUXOYKMBMCWP5CPRN4T4MAI5ZMO33TI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-KUD",
            "latitude": 52.503825,
            "longitude": 13.405409,
            "last_activity_at": "2019-10-14T10:34:24.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "KUD",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-OGTQRTA2WYUP2XPHGYZJ7E3LVSD3YC7MSH3G24Y",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-TWU",
            "latitude": 52.502218,
            "longitude": 13.407528,
            "last_activity_at": "2019-10-14T10:40:08.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 23737,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "TWU",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-BRN6EQSDNEOQ53LQ3BJVCB5PM6UIHEQNADDNQDY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-YWJ",
            "latitude": 52.498985,
            "longitude": 13.408143,
            "last_activity_at": "2019-10-14T10:39:45.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 24139,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "YWJ",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-WFCP5ESWHYIOTB6MWNMO4JLIX76VIPXISLL35EY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-DQR",
            "latitude": 52.495603,
            "longitude": 13.395287,
            "last_activity_at": "2019-10-14T10:40:53.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 40233,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "DQR",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-42AKKJAP4XLNRXFXZVOICTKD5BPAH3CX77EYL5Q",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-XNR",
            "latitude": 52.499654,
            "longitude": 13.408326,
            "last_activity_at": "2019-10-14T10:40:04.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 34198,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "XNR",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-HLGQOLTOO64YOESQFSNNSRDZM4SELUWNB7BA7ZQ",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-JHM",
            "latitude": 52.498107,
            "longitude": 13.39172,
            "last_activity_at": "2019-10-14T10:41:07.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 18104,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "JHM",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-C5SQZANHAYYGYTO6F3JF75CRTCVJJYUDB3HQAMI",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-UHW",
            "latitude": 52.498011,
            "longitude": 13.391777,
            "last_activity_at": "2019-10-14T10:40:56.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "high",
            "meter_range": 29370,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "UHW",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-AFRPJFXZ6VKCEUMOVR5OWVFID4ANS45RQAIF34Y",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-PWB",
            "latitude": 52.494716,
            "longitude": 13.400433,
            "last_activity_at": "2019-10-14T10:40:15.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 17300,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "PWB",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-F3MFTXLMS7KCFADNOZBFMN2KTQCTGQTX4IS5ULY",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-WFW",
            "latitude": 52.501872,
            "longitude": 13.391464,
            "last_activity_at": "2019-10-14T10:41:44.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 19311,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "WFW",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-BIJGT7RDLUHJKKGR2D5G6K3M2QKHCVUKPOUCJZA",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-MEE",
            "latitude": 52.498656,
            "longitude": 13.391212,
            "last_activity_at": "2019-10-14T10:40:40.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 17702,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "MEE",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-YDF7OTIQI7CDH7F2F6WJV7TYD3TUZXQI5KYLA6I",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-HHG",
            "latitude": 52.499933,
            "longitude": 13.408677,
            "last_activity_at": "2019-10-14T10:36:50.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 16093,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "HHG",
            "license_plate_number": null
          }
        },
        {
          "id": "ET-DDKPEPRWIWOFOEZFE3T3MRWW66RHITSMGY2I45Q",
          "type": "bikes",
          "attributes": {
            "status": "locked",
            "plate_number": "XXX-ELW",
            "latitude": 52.494615,
            "longitude": 13.400304,
            "last_activity_at": "2019-10-14T10:40:11.000Z",
            "bike_icon": null,
            "type_name": "scooter",
            "battery_level": "medium",
            "meter_range": 17702,
            "rate_plan": "\u20ac1 to unlock +\n\u20ac0.20 \/ 1 min",
            "rate_plan_short": "<b><font color='#7AD319' size='16' face='Montserrat'>\u20ac1<\/font><\/b><font color='#444A57' size='12' face='Montserrat'> unlock + <\/font><b><font color='#7AD319' size='16' face='Montserrat'>\u20ac0.20 <\/font><\/b> <font color='#444A57' size='12' face='Montserrat'> \/ 1 min<\/font>",
            "bike_icon_id": 6,
            "last_three": "ELW",
            "license_plate_number": null
          }
        }
      ],
      "selected_bike": null,
      "parking_spots": null,
      "icons": [
        {
          "id": "1",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/default_pin.png?fingerprint=92bcf96642bd8a61eb4f4cca70794496",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        },
        {
          "id": "2",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/default_cluster.png?fingerprint=ee1ba7d312070752ad24fd4ef1eb4cc3",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        },
        {
          "id": "3",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/billy_pin.png?fingerprint=c8d8e603a165a9e0ab8cade67302d641",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        },
        {
          "id": "4",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/bag_pin.png?fingerprint=979b39cf4be0297bc333ac392385496b",
            "description_icon_url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/descriptions\/header_bag.png?fingerprint=6fa66737de2752c3b6099a17f0ad7a37",
            "description_link_url": null,
            "description": "If you ride a bonus bike for five minutes or more, you get a %{amount} off coupon!"
          }
        },
        {
          "id": "5",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/electric_pin.png?fingerprint=03879bb627b8bac33b6310df8f16af0c",
            "description_icon_url": null,
            "description_link_url": null,
            "description": "Lime-E bikes are equipped with powerful motors and rechargeable batteries, ready to go further and faster."
          }
        },
        {
          "id": "6",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/scooter_pin.png?fingerprint=be5225eac0413888e70a9d27b4fed5c8",
            "description_icon_url": null,
            "description_link_url": null,
            "description": "Simply hop on to start the ride, and get an electric boost with ease!"
          }
        },
        {
          "id": "7",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/holidays\/bonus_santa_pin.png?fingerprint=617d0c2d272476c8da566e5e9cbe6d85",
            "description_icon_url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/descriptions\/header_bag.png?fingerprint=86f278ea1983169b3464ebfa004a9492",
            "description_link_url": null,
            "description": "If you ride a bonus bike for five minutes or more, you get a %{amount} off coupon!"
          }
        },
        {
          "id": "24",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/happy_hour_scooter_pin.png?fingerprint=758c332dfe77a7bbe9a1e8e531b31858",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        },
        {
          "id": "25",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/limepod.png?fingerprint=af6642d1ad23dd149e6480e69a21b454",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        },
        {
          "id": "26",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/limebike.png?fingerprint=f98a909aafdc2fe9231879649052153e",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        },
        {
          "id": "27",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/lime_e_full.png?fingerprint=568cd8a053ea56c6e66c5614539e52fe",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        },
        {
          "id": "28",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/lime_s_full.png?fingerprint=5843bd8729fce4d7143a5b3e0f266693",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        },
        {
          "id": "37",
          "type": "icons",
          "attributes": {
            "url": "https:\/\/d22d5yy1i19g9i.cloudfront.net\/icons\/preferred_parking_pin.png?fingerprint=483c05cecc2aba9e8b35a3917aef56fa",
            "description_icon_url": null,
            "description_link_url": null,
            "description": ""
          }
        }
      ],
      "current_level": "block",
      "levels": {
        "region": 7,
        "subregion": 11,
        "city": 14
      },
      "most_recent_trip": null,
      "banner": null,
      "donation_organization": null,
      "parking_spots_radius_meters": 20
    }
  },
  "meta": {
    "latest_user_agreement_version": "2",
    "min_ios_version": "2.11.0",
    "min_android_code": 93,
    "flags": "IOS_VERSION_V1.0,ANDROID_VERSION_V1.0",
    "groups": {
      "area_rate_plan_on_scanner": true,
      "enable_promo_notification_optout": true,
      "show_auto_reload": true,
      "map_levels_v1": true,
      "apple_pay": true,
      "show_lock_indicator": false,
      "map_balance_icon": false,
      "force_location_permission_v1": false,
      "unlock_button_group": "white_bar",
      "braze_integration": true,
      "ring_button_group": "louder_with_tooltip",
      "default_to_unlock_group": "control",
      "take_photo": "find_my_ride",
      "show_battery_level_on_map": true,
      "unlock_confirmation": false,
      "short_stop": true,
      "bluetooth_unlock": true,
      "lime_t_bluetooth_short_stop": true,
      "parked_or_not": false,
      "branch_link_referral": true,
      "persist_rate_ride": true,
      "no_header_map": true,
      "donation_group": "control",
      "fetch_end_trip_experience": false,
      "long_pause_group": false,
      "group_ride": true,
      "group_ride_v2": false,
      "group_ride_max_rider_cap": "5",
      "group_ride_max_guest_cap": "10",
      "paypal_payment_method": true,
      "enable_stripe_sca_flow": true,
      "id_scanner": "google_vision",
      "id_scan_show_manual_delay_sec?": 15,
      "new_method_completing_trip": true,
      "cvv_optional": false,
      "payment_creation_ui": true,
      "payment_billing_address": false,
      "payment_cardholder_name": false,
      "payment_zip_code": false,
      "payments": {
        "cvv_optional": false,
        "payment_creation_ui": true,
        "payment_billing_address": false,
        "payment_cardholder_name": false,
        "payment_zip_code": false,
        "payment_card_io_scan": false
      },
      "lime_t_whitelisted": true,
      "map_design_v3": false,
      "scooter_reservation": true,
      "pod_reservation": true,
      "use_moshi": false,
      "android_trip_events_refactor": false,
      "android_how_to_ride_tutorial": true,
      "timeout_retry": false,
      "cancel_reserve_red_button": true,
      "show_loyalty": true,
      "show_loyalty_spend_points": false,
      "show_self_help": false,
      "zone_messaging_enabled": false,
      "ride_history_with_pagination": false,
      "map_style_with_poi": false,
      "comfort_ride_enabled": false,
      "customized_speed_cap_enabled": false,
      "new_relic_logging_enabled": false,
      "recommend_nearby_bike_v2": false,
      "juicer_satellite_mode": true,
      "juicer_level_2": true,
      "juicer_reservation_v1_ios": false,
      "juicer_reservation_v1_android": false,
      "juicer_reservation_collected_limes_ios": false,
      "juicer_reservation_collected_limes_android": false,
      "juicer_reserved_android_filter": false,
      "juicer_reserved_ios_filter": false,
      "ios_juicer_rebalance_v1": false,
      "android_juicer_rebalance_v1": false,
      "juicer_hide_scooter_details": false,
      "enable_juicer_mock_gps_blocker": true,
      "juicer_earnings_notification": true,
      "enable_juicer_settings": true,
      "enable_juicer_in_app_message": true,
      "ios_juicer_multi_task_v1": true,
      "android_juicer_multi_task_v1": true,
      "complete_trip_before_take_photo": true,
      "android_upload_juicer_attributes": true,
      "enable_juicer_endpoint_v2": true,
      "juicer_bluetooth_unlock": false,
      "android_enable_backend_driven_cancel_task": true,
      "android_tooltip_v2": true,
      "android_enable_bulk_scan_of_deploy_tasks": null
    },
    "trip_id": null,
    "trip_status": null,
    "group_id": null,
    "group_ride_status": null,
    "notifications": [
      
    ],
    "messages": [
      {
        "message_token": "WWSXDGHWFABTM",
        "title": "Ride More, Pay Less",
        "image_title": "image_title",
        "lifecycle": "asap",
        "body": "Receive unlimited free unlocks for only \u20ac4.99 with the Lime Week Pass.",
        "user_input": false,
        "image_url": "https:\/\/limebike-web-public-assets.s3-us-west-1.amazonaws.com\/messages\/g2cmdunhe0n%403x.png",
        "image_medium_url": "https:\/\/limebike-web-public-assets.s3-us-west-1.amazonaws.com\/messages\/w4ujyd41e4%402x.png",
        "image_small_url": "https:\/\/limebike-web-public-assets.s3-us-west-1.amazonaws.com\/messages\/dfchuo6v49o%401x.png",
        "layout_type": "basic",
        "button_action": "app_link",
        "button_text": "Learn More",
        "text_input_hint": "",
        "option_text": "",
        "button_action_link": {
          "link": "limebike:\/\/limelab?url_to_open=https:\/\/webviews.lime.bike\/module\/limepass"
        },
        "button_action_email": null
      }
    ],
    "country_code": "",
    "user_agreement_version": 2,
    "user_agreement_country_code": "",
    "need_to_show_agreement": false,
    "user_agreement_url": "https:\/\/li.me\/user-agreement\/",
    "user_agreement_title": "We've Updated Our User Agreement",
    "user_agreement_message": "By tapping \"I Agree\" You confirm that You have read, understood, and agreed to Lime\u2019s updated User Agreement.",
    "user_agreement_primary_button": "I Agree",
    "user_agreement_view_terms_button": "View Agreement",
    "need_to_show_group_ride_agreement": true
  }
}


