# rust-gcp-iot

A sample device in rust for sending data to Google Cloud IoT Core over MQTT.

## 事前準備:

On ubuntu:

-   openssl (libssl-dev)
-   wget
-   [rust compiler](https://www.rust-lang.org)
-   pkg-config
-   git

-   Rust ラズパイ 4 に DHT11 センサを取り付けて温湿度を GCP に PubSub してみる

# How to run:

1. `gen_keys.sh`.
2. `gcloud iot devices create DEVICE_ID --project=PROJECT_ID --region=REGION --registry=REGISTRY_ID --public-key path=rsa_cert.pem,type=rs256`
3. `src/main.rs` のグローバル変数に上記の値を埋め込む
4. `cargo run`

Google Cloud project 新規作成:

1. `gcloud projects create PROJECT_ID --enable-cloud-apis` (you can add `--set-as-default`)
2. `gcloud pubsub topics create TOPIC_ID`
3. `gcloud pubsub subscriptions create projects/PROJECT_ID/subscriptions/SUBSCRIPTION_ID --topic=TOPIC_ID`
4. `gcloud iot registries create my-registry --project=PROJECT_ID --region=REGION --event-notification-config=topic=projects/PROJECT_ID/topics/TOPIC_ID`
