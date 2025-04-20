Employee Attrition Analysis – Jaya Jaya Maju

## 📌 1. Business Understanding
Departemen HR dari perusahaan Jaya Jaya Maju mengalami tantangan dalam mempertahankan karyawan. Beberapa karyawan keluar tanpa tanda-tanda yang jelas sebelumnya. Untuk mengurangi tingkat turnover, diperlukan analisis mendalam untuk mengetahui faktor-faktor yang menyebabkan karyawan keluar.

Business Objective:
Mengidentifikasi faktor-faktor yang berpengaruh terhadap keputusan karyawan untuk keluar dari perusahaan.

Data Science Objective:
Membangun model prediktif untuk mengklasifikasikan apakah seorang karyawan akan bertahan atau keluar dari perusahaan.

🧹 2. Data Understanding & Data Cleaning
Dataset berisi informasi demografis, pekerjaan, dan kompensasi dari karyawan. Tahapan yang dilakukan:

Mengimpor data

Menampilkan info tipe data & missing values

Melihat distribusi target (Attrition)

Menangani missing values dengan imputasi

Menghapus kolom yang tidak relevan seperti EmployeeId, StandardHours, dan EmployeeCount

Encoding pada variabel kategorikal menggunakan one-hot encoding

📊 3. Exploratory Data Analysis (EDA)
Beberapa insight dari EDA:

Karyawan muda cenderung lebih banyak keluar.

Karyawan dengan pengalaman kerja sedikit lebih rentan terhadap attrition.

Karyawan yang sering lembur atau bepergian memiliki kemungkinan keluar lebih tinggi.

EDA divisualisasikan dengan seaborn dan matplotlib (disertakan dalam notebook).

🧠 4. Data Preprocessing & Feature Engineering
Variabel target (Attrition) dikonversi ke format numerik: Bertahan = 0, Keluar = 1

One-hot encoding dilakukan untuk kolom kategorikal

Missing values ditangani dengan SimpleImputer menggunakan strategi most_frequent

Dataset dipecah menjadi X (fitur) dan y (target)

Pembagian data: 80% train dan 20% test, dengan stratify=y

🤖 5. Modeling
Model yang digunakan: Logistic Regression

python
Copy
Edit
from sklearn.linear_model import LogisticRegression
model = LogisticRegression(max_iter=2000)
model.fit(X_train, y_train)
📈 6. Evaluation
python
Copy
Edit
from sklearn.metrics import classification_report, confusion_matrix, accuracy_score

y_pred = model.predict(X_test)

print("Accuracy Score:", accuracy_score(y_test, y_pred))
print("\nConfusion Matrix:\n", confusion_matrix(y_test, y_pred))
print("\nClassification Report:\n", classification_report(y_test, y_pred))
Hasil Evaluasi:

Accuracy: 85.8%

Precision, Recall, dan F1-score menunjukkan performa model cukup baik untuk mendeteksi karyawan yang akan keluar

Confusion Matrix menunjukkan keseimbangan klasifikasi antara kelas 'Keluar' dan 'Bertahan'

🚀 7. Deployment
Model dijalankan secara lokal. Untuk penggunaan lebih lanjut, model bisa disimpan dengan joblib atau pickle untuk digunakan dalam sistem internal HR.

python
Copy
Edit
import joblib
joblib.dump(model, 'logistic_model.pkl')

✅ 8. Conclusion
Model logistic regression yang dibangun mampu mengklasifikasikan karyawan yang berpotensi keluar dengan akurasi 85.8%. Faktor-faktor seperti usia, pengalaman kerja, dan frekuensi lembur menjadi indikator utama dalam prediksi. Dengan hasil ini, departemen HR dapat:

Menyusun strategi retensi yang lebih baik

Menindaklanjuti karyawan dengan risiko tinggi keluar

Mengoptimalkan proses rekrutmen dan pelatihan
