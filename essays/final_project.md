---
layout: essay
type: essay
title: "Final Project Extra Credit"
date: 2025-11-04
published: True
labels:
  - Software Engineering
  - Nextjs
---

## Overview
*The problem:* Many new and transfer students at UH Mānoa struggle to find guidance during their transition. While advisors provide academic help, students often lack peer mentors who can share real experiences about courses, professors, dorm life, and campus resources. This results in unnecessary stress, misinformation, and isolation, especially during the first semester.

*The solution:* Mānoa Mentor bridges the gap between new students and experienced upperclassmen through a mentorship matching system. Using a profile-based algorithm, students can be paired with mentors who share similar majors, interests, or goals. Mentors and mentees can chat, schedule meetups, and share study tips or campus advice—all within an easy-to-use Next.js web app.

## Name of Proposers
- Lawrence Zheng  
- Jia Jun Li  
- Joshua Chow  
- Colbren Fujimoto  

## Approach
For this app, we will build a Next.js + React web platform hosted on GitHub Pages. The system will feature authentication, user profiles, and a matching algorithm that recommends mentors based on shared tags and availability. Bootstrap 5 will be used for styling and layout consistency.

There will be three main roles:
- Mentees – new students who sign up, fill out a short profile (major, interests, goals), and request a mentor.  
- Mentors – experienced students who register to guide others, manage requests, and chat with their mentees.  
- Admins – can approve mentor applications and monitor interactions for safety and integrity.  

Some possible mockup pages include:
- Landing Page (with login and mission statement)  
- Profile Creation Page  
- Mentor Search/Recommendation Page  
- Chat Page  
- Admin Dashboard  

## Use Case Ideas
- A new student creates a profile selecting their major and preferred mentor traits.  
- The system recommends a list of mentors with shared interests.  
- The mentee sends a connection request to a mentor.  
- The mentor accepts, and both can chat and schedule a meetup.  
- Admin reviews mentor activity logs to ensure mentorship quality and safety.  

## Beyond the Basics
After implementing the core features, we can expand the system with:
- AI-based mentor recommendations using personality or interest similarity metrics.  
- A scheduling system integrated with Google Calendar for setting up meetings.  
- A rating and feedback system for mentor/mentee experiences.  
- A community forum for open Q&A and study group formation.  
- Mobile-friendly PWA (Progressive Web App) support for on-the-go access.  
