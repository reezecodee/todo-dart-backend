pipeline {
    agent any

    stages {
        // 1. Persiapan: Ambil kodingan terbaru dari GitHub
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        // 2. Install Dependencies: Download library yang dibutuhkan (dart pub get)
        stage('Install Dependencies') {
            steps {
                echo '📦 Sedang mendownload library...'
                sh 'dart pub get'
            }
        }

        // 3. Static Analysis: Cek typo, syntax error, atau aturan koding yang dilanggar
        stage('Analyze Code') {
            steps {
                echo '🔍 Mengecek kualitas kode (Linter)...'
                sh 'dart analyze'
            }
        }

        // 4. Unit Test: Menjalankan semua file di folder /test
        stage('Run Unit Tests') {
            steps {
                echo '🧪 Menjalankan Unit Test...'
                sh 'dart test'
            }
        }
    }

    // Notifikasi hasil akhir di console Jenkins
    post {
        always {
            echo 'Selesai menjalankan pipeline.'
        }
        success {
            echo '✅ Mantap Mas Atyla! Semua test lolos.'
        }
        failure {
            echo '❌ Waduh! Ada test yang gagal. Cek kodinganmu lagi.'
        }
    }
}