# 🛡️ Network Intrusion Detection System (NIDS) – IBM Watson ML

This project implements a machine learning-based **Network Intrusion Detection System** to identify malicious activity in network traffic data. The model is trained, deployed, and tested using IBM Watson Machine Learning.

---

## ⚙️ Requirements

* IBM Cloud account
* IBM Watson Studio (Lite plan or above)
* IBM Watson Machine Learning service
* Python 3.x
* Required Python packages:

  * pandas
  * scikit-learn
  * joblib
  * requests
  * zipfile

---

## 📌 Features Used

The model uses the following features:

```
["duration", "protocol_type", "service", "flag", "src_bytes", "dst_bytes", "land", "wrong_fragment",
"urgent", "hot", "num_failed_logins", "logged_in", "num_compromised", "root_shell", "su_attempted",
"num_root", "num_file_creations", "num_shells", "num_access_files", "num_outbound_cmds",
"is_host_login", "is_guest_login", "count", "srv_count", "serror_rate", "srv_serror_rate",
"rerror_rate", "srv_rerror_rate", "same_srv_rate", "diff_srv_rate", "srv_diff_host_rate",
"dst_host_count", "dst_host_srv_count", "dst_host_same_srv_rate", "dst_host_diff_srv_rate",
"dst_host_same_src_port_rate", "dst_host_srv_diff_host_rate", "dst_host_serror_rate",
"dst_host_srv_serror_rate", "dst_host_rerror_rate", "dst_host_srv_rerror_rate"]
```

---

## 🧠 Model Training

* **Model**: RandomForestClassifier (or your selected ML model)
* **Scaler**: StandardScaler
* **Label Encoder**: For the `class` column (normal → 1, anomaly → 0)
* Trained on preprocessed `train_data.csv`

---

## 🚀 Model Deployment

1. Upload `nids_model_bundle.zip` (contains model, scaler, encoder) to IBM Watson Studio.
2. Deploy the model via Watson Machine Learning → Create Deployment.
3. Note the endpoint URL and API key.

---

## 🧪 Testing via Python

Use the `test.py` script with your API key to send test data:

```bash
python test.py
```

### Sample JSON Payload:

```json
{
  "input_data": [
    {
      "fields": [...],
      "values": [
        [0, 0, 2, 1, 181, 5450, 0, 0, 0, ...]
      ]
    }
  ]
}
```

### Sample Response:

```json
[
  {
    "fields": ["prediction"],
    "values": [[[0.399]]]
  }
]
```

> A value below `0.5` implies **anomaly**, otherwise **normal**.

---

## 📥 Downloading Files

To download files like `nids_model_bundle.zip` from Watson Studio:

* Click ☰ → File → Open File Browser → Right-click the file → **Download**

---

## 🛠 Future Improvements

* Auto-label output (not just probabilities)
* Support categorical features directly (via one-hot encoding or embedding)
* Extend to multi-city NIDS applications
* Visual dashboard for real-time monitoring

---

## 📚 References

* [IBM Watson Studio Documentation](https://dataplatform.cloud.ibm.com/docs/)
* NSL-KDD / KDDCup 1999 Dataset
* scikit-learn: [https://scikit-learn.org](https://scikit-learn.org)
* [Pandas Documentation](https://pandas.pydata.org)
