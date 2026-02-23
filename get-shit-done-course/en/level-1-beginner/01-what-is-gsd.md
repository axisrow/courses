---
title: "What is Get Shit Done and Why You Need It"
level: 1
lesson: 1
language: en
tags: [gsd, introduction, context-rot]
---

# What is Get Shit Done and Why You Need It

## Introduction

You write a prompt in Claude Code, get a great result. Then another. And another. But after 30-40 messages, quality starts dropping — responses get shorter, code gets worse, and the model "forgets" earlier decisions. This is called **context rot**.

**Get Shit Done (GSD)** is a meta-prompting and context engineering system that solves this problem. It gives Claude (or another AI agent) exactly the context it needs, at exactly the right moment.

## What GSD Does

- Breaks work into atomic tasks, each in a fresh context window
- Manages project state through markdown files
- Orchestrates sub-agents: researchers, planners, executors
- Automatically commits each task

## The Context Rot Problem

| Without GSD | With GSD |
|-------------|----------|
| One long conversation | Many short sessions |
| Context fills up | Each task gets fresh 200k tokens |
| Quality degrades | Quality stays consistent |
| Manual management | Automatic orchestration |

## Who This Is For

GSD is for people who want to describe an idea and have it built correctly — without pretending they're running a 50-person engineering org.

## Summary

- GSD is a meta-prompting system for Claude Code, OpenCode, and Gemini CLI
- Solves context degradation (context rot)
- Breaks work into atomic tasks with clean context
- No programming knowledge required
