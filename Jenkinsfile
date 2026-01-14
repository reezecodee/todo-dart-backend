pipeline {
    agent any

    stages {
        // 1. Persiapan: Ambil kodingan terbaru dari GitHub
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        // 2. Install Dependencies: Menggunakan 'bat' karena berjalan di Windows
        stage('Install Dependencies') {
            steps {
                echo '📦 Sedang mendownload library...'
                bat 'dart pub get'
            }
        }

        // 3. Static Analysis: Cek kualitas kode
        stage('Analyze Code') {
            steps {
                echo '🔍 Mengecek kualitas kode (Linter)...'
                bat 'dart analyze'
            }
        }

        // 4. Unit Test: Menjalankan test di Windows
        stage('Run Unit Tests') {
            steps {
                echo '🧪 Menjalankan Unit Test...'
                bat 'dart test'
            }
        }
    }

    // Notifikasi hasil akhir
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
