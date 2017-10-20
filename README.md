household_power_consumption <- read.table("household_power_consumption.txt", header = TRUE, sep = ";", stringsAsFactors = FALSE, dec = ".")
subsetdata <- household_power_consumption[household_power_consumption$Date %in% c("1/2/2007", "2/2/2007"),]
Globalactivepower <- as.numeric(subsetdata$Global_active_power)
png("plot1.png", width=480, height=480)
hist(Globalactivepower, col="red", main="Global Active Power", xlab="Global Active Power (kilowatts)")
##plot 1

datetime <- strptime(paste(subsetdata$Date, subSetData$Time, sep=" "), "%d/%m/%Y %H:%M:%S") 
png("plot2.png", width=480, height=480)
plot(datetime, Globalactivepower, type="l", xlab="", ylab="Global Active Power (kilowatts)")
##plot 2

submetering1 <- as.numeric(subsetdata$Sub_metering_1)
submetering2 <- as.numeric(subsetdata$Sub_metering_2)
submetering3 <- as.numeric(subsetdata$Sub_metering_3)
png("plot3.png", width=480, height=480)
plot(datetime, submetering1, type="l", ylab="Energy Submetering", xlab="")
lines(datetime, submetering2, type="l", col="red")
lines(datetime, submetering3, type="l", col="blue")
legend("topright", c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"), lty=1, lwd=2.5, col=c("black", "red", "blue"))
##plot 3

Globalreactivepower <- as.numeric(subsetdata$Global_reactive_power)
Voltage <- as.numeric(subsetdata$Voltage)
png("plot4.png", width=480, height=480)
par(mfrow = c(2, 2)) 
plot(datetime, Globalactivepower, type="l", xlab="", ylab="Global Active Power", cex=0.2)
plot(datetime, Voltage, type="l", xlab="datetime", ylab="Voltage")
plot(datetime, submetering1, type="l", ylab="Energy Submetering", xlab="")
legend("topright", c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"), lty=, lwd=2.5, col=c("black", "red", "blue"), cex=0.5)
lines(datetime, submetering2, type="l", col="red")
lines(datetime, submetering3, type="l", col="blue")
plot(datetime, Globalreactivepower, type="l", xlab="datetime", ylab="Global_reactive_power")
##plot 4
