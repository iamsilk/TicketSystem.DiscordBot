node {
    stage('Clone repository') {
        git branch: 'main', credentialsId: 'github-app-IAmSilK', url: 'https://github.com/IAmSilK/TicketSystem.DiscordBot'
    }
    
    stage('Login to GitHub Container Registry') {
        withCredentials([usernamePassword(credentialsId: 'GitHub-IAmSilK-Packages', passwordVariable: 'PAT', usernameVariable: 'USERNAME')]) {
            sh '''
                echo $PAT | docker login ghcr.io -u $USERNAME --password-stdin
            '''
        }
    }

    stage('Pull container') {
        sh '''
            docker pull ghcr.io/iamsilk/ticketsystem-discordbot:latest
        '''
    }

    stage('Deploy container') {
        sh '''
            docker-compose up -d
        '''
    }
}